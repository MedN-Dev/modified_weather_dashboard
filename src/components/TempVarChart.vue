<template>
  <div class="custom-card header-card card">
    <div class="card-body pt-0">
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
          "theme": "fusion",
          "showaxislines": "1",
          "numberSuffix": "°C",
          "anchorBgColor": "#6297d9",
          "paletteColors": "#6297d9",
          "rotateLabels": "1",
        },
        "data": [],
      },
    };
  },
  methods: {
    setChartData: function() {
      var data = [];
      for (var i = 0; i < this.tempVar.tempToday.length; i++) {
        var dataObject = {
          "label": this.tempVar.tempToday[i].hour,
          "value": this.tempVar.tempToday[i].temp
        };
        data.push(dataObject);
      }
      this.tempChartData.data = data;
    },
  },
  mounted: function() {
    this.setChartData();
  }, 
  watch: {
    tempVar: {
      handler: function() {
        this.setChartData();                                    
      },
      deep: true
    },
  },
};
</script>

<style>
</style>
