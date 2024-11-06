<script setup lang="ts">
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'

const props = defineProps<{
  label: string
  theme: 'black' | 'white'
  leftIcon?: string
  rightIcon?: string
  bordered?: boolean
  width?: string
  height?: string
  disabled?: boolean
  loading?: boolean
  type?: 'button' | 'submit'
  target?: string
}>()

const emits = defineEmits<{
  (e: 'click'): Promise<void>
}>()
const onclick = () => {
  if (props.disabled || props.loading) {
    return
  }

  emits('click')
  if (props.target) {
    location.href = props.target
  }
}

const getWidth = () => props.width ?? '230px'
const getHeight = () => props.height ?? '50px'
const getBackgroundColor = () => {
  if (props.theme === 'black') return '#333'
  else if (props.theme === 'white') return '#fff'
}
const getTextColor = () => {
  if (props.theme === 'black') return '#fff'
  else if (props.theme === 'white') return '#333'
}
</script>

<template>
  <button
    class="sh-btn"
    :class="{ bordered }"
    :disabled="disabled || loading"
    :type="type || 'button'"
    @click="onclick"
  >
    <template v-if="loading">
      <div class="loading-animation" />
    </template>
    <template v-else>
      <font-awesome-icon v-if="leftIcon" :icon="leftIcon" />
      <span style="padding: 0 8px">{{ label }}</span>
      <font-awesome-icon v-if="rightIcon" :icon="rightIcon" />
    </template>
  </button>
</template>

<style scoped lang="scss">
.sh-btn {
  width: v-bind(getWidth());
  height: v-bind(getHeight());
  background-color: v-bind(getBackgroundColor());
  color: v-bind(getTextColor());

  border-radius: 5px;
  text-align: center;

  &:hover,
  &:focus {
    filter: brightness(1.3);
  }

  &:disabled {
    filter: brightness(0.9);
    cursor: not-allowed;
  }
}

.bordered {
  border: 1px solid #808080;
}

.loading-animation {
  height: 50%;
  aspect-ratio: 1;
  margin: 0 auto;
  border-radius: 50%;
  border: 3px solid;
  border-color: v-bind(getTextColor());
  border-top-color: transparent;
  animation: spinner 1.5s linear infinite;
}
@keyframes spinner {
  to {
    transform: rotate(360deg);
  }
}
</style>
