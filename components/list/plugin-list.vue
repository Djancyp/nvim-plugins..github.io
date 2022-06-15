<template>
  <div class="relative w-full container">
    <span class="absolute top-0 right-0 text-xs font-bold text-green-700">
      {{ totalCount }}/{{ searchCount }}
    </span>
    <ul
      class="mt-10 container grid  gap-4 md:grid-cols-3 sm:grid-cols-1 xs:grid-cols-1"
    >
      <li
        v-for="plugin in list"
        :key="plugin.repo"
        class="relative shadow-xl border-gray-200 rounded"
      >
        <a
          :href="'https://github.com/' + plugin.repo"
          target="_blank"
          class="p-10 flex flex-col"
        >
          <span class="absolute top-2 right-2 text-xs text-gray-900 font-bold">
            {{ plugin.author }}
          </span>
          <span class="absolute bottom-1 right-1 text-xs text-gray-900"
            >Preconfigured Configurations</span
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
    totalCount: {
      type: Number,
      required: true,
    },
    searchCount: {
      type: Number,
      required: true,
    },
  },
}
</script>
