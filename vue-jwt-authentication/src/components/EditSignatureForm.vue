<!-- eslint-disable vue/no-multiple-template-root -->
<!-- eslint-disable vue/no-parsing-error -->
<!-- eslint-disable vue/no-mutating-props -->
<template>
  <h5 slot="header" class="title">Signature</h5>
  <div class="row">
    <div class="col-md-12 pr-md-1">
      <p class="oneh">인증된 Signature를 작성하세요.</p>
      <textarea class="form-control" id="" cols="30" rows="10" placeholder=""></textarea>
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
};
</script>
<style></style>
