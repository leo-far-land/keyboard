<template>
<div class="d-flex justify-content-center">
   <div class="input-group" style="width: 500px; height: 100px; padding: 10px;">
    <textarea
      class="form-control"
      aria-label="With textarea"
      style="resize: none;"
      v-model="text"
    >
    </textarea>
  </div>
</div>
</template>

<script>
export default {
  props: ["text"],
};
</script>