<template>
    <div class="box has-text-weigth-bold">
      <slot></slot>
    </div>
</template>

<script>

import { defineComponent } from 'vue';

export default defineComponent ({
  name: 'RenderBox'
})

</script>
<style scoped>
.box {
  background-color: rgb(188, 184, 184);
}
</style>