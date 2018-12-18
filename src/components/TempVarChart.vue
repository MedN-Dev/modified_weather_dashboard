<template>
  <div class="custom-card header-card card">
    <div class="card-body pt-0">
      <div class="content-header h4 text-center pt-2 pb-3">Temperature</div>
      <fusioncharts
        type="spline"
        width="100%"
        height="100%" 
        dataformat="json" 
        :datasource="tempChartData"
      >
      </fusioncharts>
    </div>
  </div>
</template>

<script>
export default {
  props: ["tempVar"],
  components: {},
  data() {
    return {
      tempChartData: {
        "chart": {
          "caption": "Temperature",
          "subCaption": "Hourly Variation",
          "anchorradius": "5",
          "showHoverEffect": "1",
          "showvalues": "1",
          "theme": "fusion",
          "showaxislines": "1",
          "numberSuffix": "°C",
          "anchorBgColor": "#72D7B2",
          "paletteColors": "#72D7B2"
        },
        "data": [],
      },
    };
  },
  methods: {
    setTempData: function() {
      this.tempChartData.data = [];
      for (var i = 0; i < this.tempVar.tempToday.length; i++) {
        var data_object = {
          "label": this.tempVar.tempToday.hour, 
          "value": this.tempVar.tempToday.temp
        };
        this.tempChartData.data.push(data_object);
      };
    },
  }, 
  watch: {
    tempVar: {
      handler: function() {
        this.tempChartData.data = [];
        for (var i = 0; i < this.tempVar.tempToday.length; i++) {
          var data_object = {
            "label": this.tempVar.tempToday.hour, 
            "value": this.tempVar.tempToday.temp
          };
          this.tempChartData.data.push(data_object);
        };
      },
      deep: true
    },
  },
};
</script>

<style>
</style>
