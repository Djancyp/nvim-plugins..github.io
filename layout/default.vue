<template>
  <div class="layout">
    <catMenu :menu="menu" />
    <SearchBar @search="sortSearch" />
    <List :list="listPlugins" />
  </div>
</template>
<script>
import SearchBar from '../components/searchbar/search-bar.vue'
import catMenu from '../components/menu/cat-menu.vue'
import List from '../components/list/plugin-list.vue'
// import menu from '../data/menu/menu.js'
// import Plugins from '../data/plugins/plugins.js'
export default {
  name: 'DefaultLayout',
  components: {
    SearchBar,
    catMenu,
    List,
  },

  data() {
    return {
      menu: [
        {
          displayName: 'Plugin Manager',
          category: 'plugin_manager',
        },
        {
          displayName: 'LSP',
          category: 'LSP',
        },
        {
          displayName: 'Completion',
          category: 'completion',
        },
      ],
      plugins: [
        {
          displayName: 'numToStr/Comment.nvim',
          repo: 'numToStr/Comment.nvim',
          description: 'A simple plugin to convert numbers to strings.',
          tags: ['javascript', 'comment', 'web development'],
        },
        {
          displayName: 'LSP Installer',
          description: 'A simple plugin to install LSP',
          repo: 'B',
          tags: ['lsp', 'language server'],
        },
        {
          displayName: 'New Plugin',
          description: 'A simple plugin to install LSP',
          repo: 'C',
          tags: ['lsp', 'language server'],
        },
      ],
      listPlugins: this.plugins,
    }
  },
  methods: {
    sortSearch(val) {
      if (val) {
        // add only this.plugins.tags matching the search
        this.listPlugins = this.plugins.filter((plugin) => {
          return plugin.tags.some((tag) =>
            tag.toLowerCase().includes(val.toLowerCase())
          )
        })
      } else {
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
