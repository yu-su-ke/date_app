<template>
  <div>
    <div class="form-horizontal">
      <div class="form-group">
        <label class="col-md-2 control-label">Time Zone</label>
        <div class="col-md-10">
          <p>UTC<input type="text" size="3" readonly class="form-control" v-model="time"/>00</p>
          <div class="help-block">
            <input type="range" min="-12" max="12" step="1" v-model.number="h" />
          </div>
        </div>
      </div>
    </div>
    <clock :message="{hours, day}"></clock>
  </div>
</template>

<script>
  import Clock from './Clock.vue';

  export default {
    components: {
      Clock
    },
    data(){
      return{
        h: 0,
        date: new Date(),
      }
    },
    computed: {
      time: function() {
        //return `${this.h}`
        if(this.h < 0){
          if(this.h > -10){
            return ("-0" + Math.abs(this.h)).slice(-3)
          }else{
            return "-" + Math.abs(this.h)
          }
        }else{
          if(this.h < 10){
            return ("+0" + this.h).slice(-3)
          }
          return ("+" + this.h).slice(-3)
        }
      },
      day: function() {
        if(this.date.getUTCHours() + this.h >= 24){
          return this.date.getUTCDate() + 1;
        }else{
          return this.date.getUTCDate();
        }
      },
      hours: function() {
        if(this.date.getUTCHours() + this.h >= 24){
          return this.date.getUTCHours() + this.h - 24
        }else{
          return this.date.getUTCHours() + this.h
        }
      },
    },
    mounted() {
      this.setDate();
      setInterval(() => this.setDate(), 1000)
    },
    methods: {
      setDate() {
        this.date = new Date()
      },
    },
  }

</script>

<style scoped>

  /*バーのサイズ、設定*/
  input[type="range"] {
    -webkit-appearance:none;
    /*右に伸ばす*/
    width: 96%; background: #eee;
    box-shadow: 0 0 10px #666;
    border-radius: 50px;
  }

  /*ボタンのサイズ*/
  input[type="range"]::-webkit-slider-thumb {
    -webkit-appearance: none;
    background: #333;
    width: 20px;
    height: 20px;
    border-radius: 50%;
  }

  input[type="range"]::-webkit-slider-thumb:hover {
    background: #999;
  }

  input[type="range"]::-webkit-slider-thumb:active {
    background: #fefefe;
  }

  .col-md-2{
    font-size: 2.0em;
  }

  .form-control{
    font-size: 1.2em;
  }




</style>
