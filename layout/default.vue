<template>
  <div class="layout">
    <catMenu :menu="menu" @filter="sortSearch" />
    <SearchBar @search="sortSearch" />
    <List
      :list="listPlugins"
      :total-count="totalCount"
      :search-count="searchCount"
    />
  </div>
</template>
<script>
import SearchBar from '../components/searchbar/search-bar.vue'
import catMenu from '../components/menu/cat-menu.vue'
import List from '../components/list/plugin-list.vue'
import menu from '../data/menu/menu.js'
import Plugins from '../data/plugins/plugins.js'
export default {
  name: 'DefaultLayout',
  components: {
    SearchBar,
    catMenu,
    List,
  },

  data() {
    return {
      menu,
      plugins: Plugins,
      listPlugins: Plugins,
      totalCount: Plugins.length,
      searchCount: Plugins.length,
    }
  },
  methods: {
    sortSearch(val) {
      if (val) {
        // add only this.plugins.tags matching the search
        this.listPlugins = this.plugins.filter((plugin) => {
          return (
            plugin.tags.some((tag) =>
              tag.toLowerCase().includes(val.toLowerCase())
            ) ||
            plugin.displayName.toLowerCase().includes(val.toLowerCase()) ||
            plugin.author.toLowerCase().includes(val.toLowerCase())
          )
        })
        this.searchCount = this.listPlugins.length
      } else {
        this.searchCount = this.totalCount
        this.listPlugins = this.plugins
      }
    },
  },
}
</script>
<style lang="css">
.layout {
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
}
</style>
