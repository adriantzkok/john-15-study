<template>
  <div>
    <div class="controlbar">
      <h1 class="studyh1">{{ header }}</h1>
    </div>
    <hr class="solid" />
    <slot></slot>
  </div>
</template>

<script>
export default {
  props: {
    header: {
      required: true
    }
  }
}
</script>

<style scoped></style>
