<template>
  <li>
    <div class="bookmark__item">
      <a :href="url" v-if="url">{{url}}</a>
      <code v-else>{{text.replace(/\#[a-zA-Z]+\s/, '')}}</code>
      <pre :class="hashtag.replace('#', '')" v-for="(hashtag, index) in tags" :key="index">{{hashtag}}</pre>
    </div>
  </li>
</template>

<script>
export default {
  data: function() {
    return {
      tags: [],
      url: '',
    }
  },
  props: {
    entities: Array,
    text: String,
    code: String,
  },
  mounted: function() {
    this.entities.forEach(entity => {
      switch(entity.type) {
        case "hashtag":
          this.tags.push(this.text.substring(entity.offset, entity.offset + entity.length));
          break;
        case "url":
          this.url = this.text.substring(entity.offset, entity.offset + entity.length);
          break;
        default:
      }
    });


  }
}
</script>

<style lang="scss" scoped>
  .bookmark__item {
    margin-bottom: 0.5rem;

    a, pre {
      display: inline;
    }

    pre {
      margin-left: 0.5rem;
      background-color: #ff79c6;

      &.golang {
        background-color: aqua;
      }

      &.js, &.javascript {
        background: #f1fa8c;
      }

      &.rails {
        background-color: #ff5555;
      }
    }

    code {
      color: #50fa7b;
      background-color: #6272a4;
    }
  }
</style>
