<template>
  <h2>綁定樣式</h2>
  <p>超過五個字的時候會顯示不同樣式。</p>
  Edit: <input
    type="text"
    v-model.trim="message"
    placeholder="請勿超過五個字"
    :style="msgStyle">
  <hr>
</template>
<script>
export default {
  data () {
    return {
      message: ''
    }
  },
  computed: {
    isVaild: function() {
      return this.message.length <= 5;
    },
    msgStyle: function() {
      return {
        'border': this.isVaild ? '' : 'red solid 1px',
        'color': this.isVaild ? '' : 'red'
      };
    }
  }
};
</script>