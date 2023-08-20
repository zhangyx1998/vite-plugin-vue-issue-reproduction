<template>
  <span>{{ message }}</span>
</template>

<script>
import { defineComponent } from 'vue';
export const component = defineComponent({
  setup(message) {
    return { message };
  }
});
export const getComponentB = (message) => {
  const { setup, ...others } = component;
  return defineComponent({
    setup() {
      return { ...setup(message) };
    },
    ...others
  });
};
export default component;
</script>