<template>
  <div :id="options.id"></div>
</template>

<script>
  export default {
    name: 'Bar-chart',
    data() {
      return {
        chart: null
      }
    },
    props: {
      options: {
        type: Object,
        required: true
      },
      data: {
        type: Array,
        required: true
      }
    },
    watch: {
      data(data) {
        this.$nextTick(() => {
          this.chart.setData(this.data);
        });
      }
    },
    mounted() {
      this.chart = Morris.Bar({
        element: this.options.id,
        data: this.data,
        xkey: this.options.xkey,
        ykeys: this.options.ykeys,
        labels: this.options.labels,
      });
    }
  }
</script>

<style>
  
</style>
