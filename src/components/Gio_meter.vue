<template>
  <div>
    <div class="form-horizontal">
      <div class="form-group">
        <label class="col-md-2 control-label">Time Zone</label>
        <div class="col-md-10">
          <input type="range" v-model="s" min="-12.0" max="12.0" step="1.0" />
          <span id="value">0</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  let elem = document.getElementsByClassName('col-md-10');
  let target = document.getElementById('value');
  let rangeValue = function (elem, target){
    return function(evt){
      target.innerHTML = elem.value;
    }
  };
    export default {
        name: "meter",
      computed: {
          let: rangeValue = function (elem, target){
          return function(evt){
            target.innerHTML = elem.value;
          }
        }
      },
      mounted(){
        elem.addEventListener('input', rangeValue(elem, target));
      }
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
