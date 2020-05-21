<template>
  <Layout>
    <bookmark-list/>
  </Layout>
</template>

<script>
import BookmarkList from "../components/Bookmark/BookmarkList";

export default {
  components: {
    BookmarkList,
  },
  metaInfo: {
    title: 'Bookmark'
  }
}
</script>

<style>
.home-links a {
  margin-right: 1rem;
}
</style>
