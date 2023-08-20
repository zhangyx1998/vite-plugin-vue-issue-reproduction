<script setup>
import ComponentA from './components/A.vue';
import { getComponentB, component as ComponentB } from './components/B.vue';
import ComponentC, { getComponentC } from './components/C.vue';
console.log("Component B", ComponentB);
console.log("Component C", ComponentC);
</script>

<template>
  <table>
    <tr style="--color: black">
      <td>
        <ComponentA />
      </td>
    </tr>
    <tr style="--color: red">
      <td>
        <component :is="getComponentB('I only render in dev mode')" />
      </td>
    </tr>
    <tr style="--color: blue">
      <td>
        <component :is="getComponentC(
          'I am a dirty fix of B. ' +
          'All I did was to console.log my default export.'
          )" />
      </td>
    </tr>
  </table>
</template>

<style>
body {
  background-color: white;
}
td {
  margin: 1em;
  padding: 0.5em 1em;
  color: var(--color);
  border: 1px solid var(--color);
  min-height: 1em;
}
</style>