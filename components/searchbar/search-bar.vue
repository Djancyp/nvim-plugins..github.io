<template>
  <div class="search-box w-full mt-10">
    <input
      ref="search"
      v-model="search"
      class="search border-2 border-2 border-gray-200"
      type="text"
      placeholder="Search Plugin"
    />
  </div>
</template>
<script>
export default {
  data() {
    return {
      search: '',
    }
  },
  watch: {
    search(newData, oldData) {
      this.$emit('search', newData)
    },
  },

  mounted() {
    this.$refs.search.focus()
  },
}
</script>
<style lang="css">
.search-box {
  display: flex;
  align-items: center;
  justify-content: center;
}
.search {
  width: 100%;
  max-width: 400px;
  height: 3em;
  border: 1px solid #ccc;
  border-radius: 5px;
  padding: 0.5em;
  font-size: 1.2em;
}
.search:focus {
  outline: none;
}
</style>
