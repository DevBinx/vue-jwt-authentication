<!-- eslint-disable vue/no-multiple-template-root -->
<!-- eslint-disable vue/no-parsing-error -->
<template>
  <h5 slot="header" class="title">Payload</h5>
  <div class="row">
    <div class="col-md-12 pr-md-1">
      <p class="oneh">Token의 데이터를 작성하세요.</p>
      <textarea v-model="payloadData.payload" class="form-control" id="" cols="30" rows="10"></textarea>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    model: Object,
  },
  data() {
    return {
      payloadData: this.model.payloadData || '',
    };
  }
};
</script>