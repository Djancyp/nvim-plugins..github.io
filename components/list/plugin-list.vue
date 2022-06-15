<template>
  <div class="">
    <ul class="w-full flex flex-wrap mt-10 container">
      <li v-for="plugin in list" :key="plugin.repo">
        <a
          :href="plugin.repo"
          class="gap-8 column-3xs m-2 flex flex-col shadow-xl p-10 border-2 border-gray-200 hover:columns-3"
        >
          <strong>{{ plugin.displayName }} </strong>
          <span>{{ plugin.description }} </span>
        </a>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  props: {
    list: {
      type: Array,
      required: true,
    },
  },
}
</script>
