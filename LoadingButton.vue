<template>
  <button :disabled="loading" class="flex justify-between items-center py-2 border-radius-xl px-4 bg-indigo-500 text-sm rounded text-gray-100 cursor-pointer hover:bg-indigo-600 hover:text-gray-100 focus:outline-none">
    <slot />
  </button>
</template>

<script>
export default {
  props: {
    loading: Boolean,
  },
}
</script>
