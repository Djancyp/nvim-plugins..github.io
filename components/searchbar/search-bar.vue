<template>
  <div class="search-box w-full mt-10 flex flex-row relative">
    <img src="../../static/images/logo.png" class="absolute logo"  />
    <input
      ref="search"
      v-model="search"
      class="search border-2 border-2 border-gray-200 shadow-xl"
      type="text"
      placeholder="Search Plugin"
    />
    <ul class="pt-5 list-disc text-blue-600">
      <li>Plugin Name</li>
      <li>Plugin Tags</li>
      <li>Plugin Author</li>
    </ul>
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
.logo{
    width: 500px;
    height: 500px;
    z-index: -1;
    bottom:100%;
}
.search-box {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
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
