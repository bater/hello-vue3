<template>
  <p>假設, 1 日幣 = 0.209 台幣, 且 1 美金 = 31.406 台幣: </p>
  <div>台幣 <input type="text" v-model="twd"></div>
  <div>日幣 <input type="text" v-model="jpy"></div>
  <div>美金 <input type="text" v-model="usd"></div>
</template>

<script>
export default {
  data() {
    return {
      twd: 1000
    }
  },
  computed: {
    jpy: {
      get() {
        return Number.parseFloat(Number(this.twd) / 0.209).toFixed(3);
      },
      set(val) {
        this.twd = Number.parseFloat(Number(val) * 0.209).toFixed(3);
      }
    },
    usd: {
      get() {
        return Number.parseFloat(Number(this.twd) / 31.406).toFixed(3);
      },
      set(val) {
        this.twd = Number.parseFloat(Number(val) * 31.406).toFixed(3);
      }
    }
  }
};
</script>
