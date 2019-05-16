<template>
  <div>
    <div class="container">
      <p class="date">{{ year }}/{{ month }}/{{ day }}</p>
      <div class="time">
        <p class="time-item hours">{{ hours }}</p>
        <p class="time-item minutes">{{ minutes }}</p>
        <p class="time-item seconds">{{ seconds }}</p>
      </div>
    </div>
  </div>
</template>

<script>

  const zeroPadding = (num, digit) => {
    return(Array(digit).join("0") + num).slice(-digit)
  };


  export default {
    data() {
      return {
        date: new Date(),
      }
    },
    computed:{
      year(){
        return this.date.getFullYear()
      },
      month(){
        return zeroPadding(this.date.getMonth() + 1, 2)
      },
      day(){
        return zeroPadding(this.date.getDate(), 2)
      },
      hours() {
        return zeroPadding(this.date.getHours(), 2)
      },
      minutes(){
        return zeroPadding(this.date.getMinutes(), 2)
      },
      seconds(){
        return zeroPadding(this.date.getSeconds(), 2)
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
  .container {
    background-color: #4169e1;
    /*background-image: url("../assets/japan.jpeg");*/
    /*background-repeat: no-repeat;*/
    padding: 2%;
  }


  .date {
    text-align: right;
    color: #fff;
    font-family: 'Luckiest Guy', cursive;
    font-size: 4rem;
    letter-spacing: .1em;
    margin: .0em 0;
    line-height: 1;
  }


  .time {
    display: flex;
  }


  .time-item {
    display: flex;
    justify-content: center;
    align-items: center;
    flex: 1 1;
    height: 100px;
    position: relative;
    z-index: 1;
    padding: 0.5em;
    margin: 3px;
    color: #000000;
    font-family: 'Luckiest Guy', cursive;
    font-size: 5rem;
    line-height: 1;
    background-color: #afeeee;
    /*background-image: url("../assets/japan.jpeg");*/
    /*background-repeat: no-repeat;*/
    box-sizing: border-box;
  }


  .time-item:before {
    position: absolute;
    right: 5px;
    bottom: 1px;
    z-index: 1;
    color: #3a4a5e;
    font-family: 'Luckiest Guy', cursive;
    font-size: 1.4rem;
    letter-spacing: .05em;
  }


  .hours:before {
    content: "Hours";
    font-size: 0.5em;
  }


  .minutes:before {
    content: "Minutes";
    font-size: 0.5em;
  }


  .seconds:before {
    content: "Seconds";
    font-size: 0.5em;
  }
</style>
