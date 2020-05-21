<template>
  <div>
    <ul>
      <bookmark-item v-for="bookmark in bookmarks" :key="bookmark.message_id" v-bind="bookmark" />
    </ul>
  </div>
</template>

<script>
import axios from "axios";
import BookmarkItem from "./BookmarkItem";

export default {
  data: function() {
    return {
      bookmarks: [],
    }
  },
  created: async function() {
    const { data: { messages } } = await axios.get("https://telegram-notes-bot.namtx.now.sh/api/get_updates")

    this.bookmarks = messages;
  },
  components: {
    BookmarkItem,
  }
}
</script>

<style scoped>
  ul {
    list-style: none;
  }
</style>
