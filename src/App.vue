<template>
  <div>
    <Clock class="clock"/>
    <Map class="map"/>
    <Gio_meter class="meter"/>
  </div>
</template>

<script>
  import Clock from "@/components/Clock"
  import Map from "@/components/Map"
  import Gio_meter from "@/components/Gio_meter"


  export default {
    components: {
      Clock,
      Map,
      Gio_meter,

    },
  }
</script>

<style scoped>
  .clock {
    width: 80%;
    max-width: 600px;
    margin: 80px auto;
  }

  .map {
    width: 100%;
    max-width: 1200px;
    margin: 80px auto;
  }
  /*.map {*/
  /*  width: 930px;*/
  /*  max-width: 900px;*/
  /*  margin: 80px auto;*/
  /*}*/

  .meter {
    width: 100%;
    /*左に伸ばす*/
    max-width: 1200px;
    margin: 80px auto;
  }

</style>


<style>
  html {
    font-size: 62.5%;
  }


  body {
    margin: 0;
  }


  p {
    margin: 0;
  }
</style>
