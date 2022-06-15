<template>
  <div>
    <ul class="top-menu container">
      <li v-for="m in menu" :key="m.repo" class="bg-green-500 shadow-md">
        <a :href="m.category" class="text-gray-200">
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
}
</script>
<style lang="css">
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
