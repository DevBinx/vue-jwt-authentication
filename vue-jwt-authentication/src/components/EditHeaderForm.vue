<!-- eslint-disable vue/no-multiple-template-root -->
<!-- eslint-disable vue/no-parsing-error -->
<!-- eslint-disable vue/no-mutating-props -->
<template>
  <h5 slot="header" class="title">Header</h5>
  <div class="row">
    <div class="col-md-12 pr-md-1">
      <p class="oneh">유효한 Header를 작성하세요.</p>
      <pre> {{ header }}</pre>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    model: {
      type: Object,
      default: () => {
        return {};
      },
    },
  },
  data() {
    return {
      header: {
        alg: "HS256",
        typ: "JWT",
      },
    };
  },
};
</script>
<style></style>
