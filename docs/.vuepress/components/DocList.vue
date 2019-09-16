<template>
  <div>
    <ul>
      <li v-for="doc in docs">
        <router-link :to="doc.path">{{ doc.title }}</router-link>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "DocList",
  computed: {
    docs() {
      const pages = this.$site.pages
        .filter(x => x.regularPath.startsWith("/notes/"))
        .sort((a, b) => (a.title > b.title ? 1 : b.title > a.title ? -1 : 0));
      return pages;
    }
  }
};
</script>