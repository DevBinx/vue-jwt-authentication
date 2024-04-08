<!-- eslint-disable vue/no-multiple-template-root -->
<!-- eslint-disable vue/no-parsing-error -->
<!-- eslint-disable vue/no-mutating-props -->
<template>
  <h5 slot="header" class="title">Encoded</h5>
  <div class="row">
    <div class="col-md-12">
      <textarea :value="encodedData" @input="$emit('generateToken', $event)" label="JWT Token" class="encodedHeight"
        cols="30" rows="10">
        </textarea>
    </div>
  </div>
  <button slot="footer" type="primary" fill @click="requestTokenGeneration">GENERATE</button>
</template>

<script>
export default {
  props: {
    model: Object,
    encodedData: String
  },
  data() {
    return {

    };
  },
  methods: {
    requestTokenGeneration() {
      this.$emit('generateToken');
    }
  }
};
</script>

<style></style>