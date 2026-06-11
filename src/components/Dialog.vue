<script setup lang="ts">
const props = defineProps<{
  modelValue: boolean;
  closeOnOverlay?: boolean;
}>();

const emit = defineEmits(["update:modelValue"]);

function close() {
  emit("update:modelValue", false);
}
</script>
<template>
  <Teleport to="body">
    <transition name="fade">
      <div
        v-if="modelValue"
        class="overlay"
        @click="closeOnOverlay ? close() : null"
      >
        <div class="dialog" @click.stop>
          <slot></slot>

          <button class="close-btn" @click="close">Fechar</button>
        </div>
      </div>
    </transition>
  </Teleport>
</template>

<style scoped>
@import '@/assets/styles/components/dialog'
</style>
