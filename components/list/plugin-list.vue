<template>
  <div class="">
    <ul class="w-full  mt-10 container grid grid-cols-6 gap-2">
      <li v-for="plugin in list" :key="plugin.repo" class="col-span-2">
        <a
          :href="'https://github.com/' + plugin.repo"
          target="_blank"
          class="m-2 flex flex-col shadow-xl p-10 border-2 border-gray-200 rounded-xl bg-blue-500 text-white"
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
