<template>
  <div class="p-4 bg-yellow-300 rounded border border-yellow-500 flex items-center justify-between">
    <div class="flex items-center">
      <icon
        name="trash"
        class="flex-shrink-0 w-4 h-4 fill-yellow-900 mr-2"
      />
      <div class="text-yellow-900">
        <slot />
      </div>
    </div>
    <button
      class="text-yellow-900 hover:underline"
      tabindex="-1"
      type="button"
      @click="$emit('restore')"
    >
      Restore
    </button>
  </div>
</template>

<script>
import Icon from '~/components/Icon'

export default {
  components: {
    Icon,
  },
}
</script>
