<template>
  <div class="highlights-item col-md-4 col-sm-6 col-xs-12 border-left border-right">
    <div>
    <div class="card-heading pt-3">Wind Status</div>
    <div class="row pt-4">
      <div class="col-sm-6 col-md-6 mt-2 text-center align-middle">
        <p class="card-sub-heading mt-3">Wind Direction</p>
        <p class="mt-3"><img src="../assets/winddirection.svg" height="30" width="30"></p>
        <p class="card-value mt-3">{{ highlights.windStatus.derivedWindDirection }}</p>
      </div>
      <div class="col-sm-6 col-md-6 mt-2">
        <p class="card-sub-heading mt-3">Wind Speed</p>
        <p class="mt-3"><img src="../assets/windspeed.svg" height="30" width="30"></p>
        <p class="card-value mt-3">{{ highlights.windStatus.windSpeed }} km/h</p>
      </div>
    </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["highlights"],
  components: {},
  data() {
    return {};
  },
  methods: {},
  computed: {}
};
</script>