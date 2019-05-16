<template>
<!--  <div id="app">-->
<!--    <div class="form-horizontal">-->
<!--      <div class="form-group">-->
<!--        <label class="col-md-2 control-label">Time Zone</label>-->
<!--        <div class="col-md-10">-->
<!--          <input class="form-control" v-model="c" :style="{backgroundColor: c}" />-->
<!--&lt;!&ndash;          <input type="range" id="range" min="-12.0" max="12.0" step="1.0" v-model.number="t"/>&ndash;&gt;-->
<!--&lt;!&ndash;          <input type="text" id="value"/>&ndash;&gt;-->
<!--          <div class="help-block">-->
<!--            <input type="range" min="0" max="360" v-model.number="h" />-->
<!--            <input type="range" min="0" max="100" v-model.number="s" />-->
<!--            <input type="range" min="0" max="100" v-model.number="l" />-->
<!--          </div>-->
<!--          <br>-->
<!--          <br>-->
<!--          <p>{{ test }}rrr</p>-->
<!--&lt;!&ndash;          <span id="value">0</span>&ndash;&gt;-->
<!--        </div>-->
<!--      </div>-->
<!--    </div>-->
<!--  </div>-->
  <div id="app">
    <div class="form-horizontal">
      <div class="form-group">
        <label class="col-md-2 control-label">Time Zone</label>
        <div class="col-md-10">
          <input class="form-control" v-model="c" :style="{backgroundColor: c}" />
          <div class="help-block">
            <input type="range" min="0" max="360" v-model.number="h" />
            <input type="range" min="0" max="100" v-model.number="s" />
            <input type="range" min="0" max="100" v-model.number="l" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  // let elem = document.getElementById('range');
  // let target = document.getElementById('value');
  // let rangeValue = function (elem, target) {
  //   return function(evt){
  //     target.innerHTML = elem.value;
  //   }
  // };
  //
  // elem.addEventListener('input', rangeValue(elem, target));

  // let rangeValue = function (elem, target) {
  //     return function(evt){
  //       target.innerHTML = elem.value;
  //     }
  //   };
  //
  // export default {
  //   data() {
  //     return {
  //       elem: document.getElementById('range'),
  //       target: document.getElementById('value'),
  //     }
  //   },
  //   computed: {
  //     test(){
  //       //return this.elem.value
  //       //return this.elem.addEventListener('input', rangeValue(this.elem, this.target))
  //     },
  //   }
  // }

  export default {
    data(){
      return{
        h: 0,
        s: 84,
        l: 77,
      }
    },
    computed: {
      c: function() {
        return `hsl(${this.h}, ${this.s}%, ${this.l}%)`
      },
    },
  }

</script>

<style scoped>

  /*バーのサイズ、設定*/
  input[type="range"] {
    -webkit-appearance:none;
    /*右に伸ばす*/
    width: 95%; background: #eee;
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


</style>
