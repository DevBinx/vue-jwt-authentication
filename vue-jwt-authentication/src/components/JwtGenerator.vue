<template>
  <div class="row">
    <div class="col-md-6">
      <edit-header-form></edit-header-form>
      <edit-payload-form :model="model"></edit-payload-form>
      <edit-signature-form></edit-signature-form>
    </div>
    <div>
      <edit-encoded-form :encodedData="model.encodedData" @generateToken="generateToken"></edit-encoded-form>
    </div>
  </div>
</template>

<script>
import EditHeaderForm from "./EditHeaderForm";
import EditPayloadForm from "./EditPayloadForm";
import EditSignatureForm from "./EditSignatureForm";
import EditEncodedForm from "./EditEncodedForm";
import axios from 'axios';

export default {
  components: {
    EditHeaderForm,
    EditPayloadForm,
    EditSignatureForm,
    EditEncodedForm,
  },
  data() {
    return {
      model: {
        // 초기 데이터 구조
        header: {
          alg: "HS256",
          typ: "JWT",
        },
        payloadData: {
          payload: ''
        },
        verify: {
          secretKey: "testestestestestestestsetestestestestestetsestestest"
        },
        encodedData: ''
      },
    };
  },
  methods: {
    generateToken() {
      // Payload가 비어있는지 확인
      if (!this.isPayloadEmpty()) {
        const header = this.model.header;
        const payload = this.model.payloadData;
        const verify = this.model.verify;

        axios.post('http://devopskim.nginxstore.kr:8089/jwt_issued', {
          header: header,
          payload: payload,
          verify: verify
        })
          .then(response => {
            console.log(response)
            this.model.encodedData = response.data;
          })
          .catch(error => {
            console.error('Error:', error);
            alert('서버와 통신 중 오류가 발생했습니다.');
          });
      } else {
        alert('Payload 값을 입력하세요.');
      }
    },

    payloadChanged(payload) {
      this.model.payloadData.payload = payload;
    },
    isPayloadEmpty() {
      return this.model.payloadData.payload.trim() === '';
    }
  },
};
</script>
