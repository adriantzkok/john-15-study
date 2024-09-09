<template>
  <div>
    <div class="controlbar">
      <h1 class="studyh1">{{ heading }}</h1>
    </div>
    <hr class="solid" />
    <div class="investigation">
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    heading: { type: String }
  }
}
</script>

<style></style>
