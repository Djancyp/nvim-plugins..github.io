<template>
  <div class="relative">
    <img src="../../static/images/logo.png" class="absolute logo" />

    <ul class="top-menu container">
      <li
        v-for="m in menu"
        :key="m.repo"
        class="shadow-md"
        :class="[m.category === category ? 'bg-green-900' : 'bg-green-500']"
      >
        <a
          class="text-gray-200 cursor-pointer"
          @click="filterCategory(m.category)"
        >
          {{ m.displayName }}
        </a>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  props: {
    menu: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      category: '',
    }
  },
  methods: {
    filterCategory(m) {
      if (this.category !== m) {
        this.category = m
      } else {
        this.category = ''
      }
      this.$emit('filter', this.category)
    },
  },
}
</script>
<style lang="css">
.logo {
  width: 500px;
  height: 500px;
  z-index: -1;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.top-menu {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: center;
  list-style: none;
  padding: 0;
  margin: 0;
}
.top-menu li {
  margin: 0.5em;
  display: flex;
  /* flex-direction: row; */
  align-items: center;
  justify-content: center;
  border: 1px solid #ccc;
  border-radius: 5px;
}
.top-menu li a {
  text-decoration: none;
  font-size: 1.2em;
  padding: 0.5em;
}
.selected {
  background-color: #3b82f6;
}
</style>
