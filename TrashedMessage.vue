<template>
  <div class="p-4 bg-red-400 rounded flex items-center justify-between lg:w-1/2">
    <div class="flex items-center">
      <icon name="trash" class="flex-shrink-0 w-4 h-4 fill-red-800 mr-2" />
      <div class="text-sm font-medium text-red-800">
        <slot />
      </div>
    </div>
    <button class="focus:outline-none text-sm text-red-800 hover:underline" tabindex="-1" type="button" @click="$emit('restore')">Restore</button>
  </div>
</template>

<script>
import Icon from '@/Jetstream/Icon'

export default {
  components: {
    Icon,
  },
}
</script>
