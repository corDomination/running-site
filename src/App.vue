<template>
<body>
  <div id="webpage">
    <top-bar>Jack's Running Site</top-bar>
      <div class="leftcolumn">
        <div class="card" id="daily-hab">
          <div id="minititle">Daily Habits</div>
          <daily-habits></daily-habits>
        </div>
      </div>
      <div class='middlecolumn'>
        <div class="card">
          <div id="minititle">Beautiful Gettler Stadium</div>
          <img src="@/assets/Gettler.jpg" alt="">
        </div>
      </div>
      <div class='rightcolumn'>
        <div class="card" id="pace-c">
          <div id="minititle">Pace Calculator</div>
          <pace-calculator></pace-calculator>
        </div>
        <div class="card" id="log-e">
          <div id="minititle">Log Entry</div>
          <new-log-entry></new-log-entry>
        </div>
      </div>
      <div class='big-column'>
        <div class="card">
          <div id="minititle">Running Log</div>
          <running-log></running-log>
        </div>
      </div>
  </div>
</body>
</template>

<script>
  import topBar from './components/topBar.vue'
  import newLogEntry from './components/newLogEntry.vue'
  import dailyHabits from './components/dailyHabits.vue'
  import paceCalculator from './components/paceCalculator.vue'
  import runningLog from './components/runningLog.vue'
  export default {
    name: 'App',
    components: {
      topBar,
      newLogEntry,
      dailyHabits,
      paceCalculator,
      runningLog
    },
    data() {
      return {}
    },
    methods: {
      calcTotalSeconds: function (hour, minute, second) {
        var totalsecs = 0;
        if (hour != null) {
          totalsecs += hour * 3600;
        }
        if (minute != null) {
          totalsecs += minute * 60;
        }
        if (second != null) {
          totalsecs += second * 1;
        }
        return totalsecs;
      }
    },
    computed: {
      "weekMileage": function weeksMiles() {
        var weeklyMileage = 0;
        for (var i = this.rows.length; i > 0; i--) {
          weeklyMileage += this.rows[i].Distance;
        }
        return weeklyMileage;
      }
    }
  }
</script>

<style>
  #app {
    display:block;
    font-family: Helvetica, Arial, sans-serif;
    font-weight: 700;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    margin-top: 60px;
  }

  html {
    min-width: 1536px;
  }

body{
  height:100vh;
  background-color:gainsboro;
}
  #webpage {
    background-color: white;
    float: left;
    margin: 0 10%;
    text-align: center;
    border-color:grey;
    border-width: 2px;
    border-style: solid;
  }

  img {
    width: 100%;
    max-height:500px;
    max-width: 810px;
  }

  .leftcolumn {
    float: left;
    width: 14%;
    margin: 0 1%;
    height: 500px;
  }

  .middlecolumn {
    float: left;
    width: 55%;
    margin: 0 1%;
    height: 500px;
  }

  .rightcolumn {
    width: 25%;
    float: left;
    margin: 0 1%;
    height: 500px;
  }

  .row:after {
    content: "";
    display: table;
    clear: both;
  }

  .big-column {
    width: 100%;
    float: left;
  }

  /* Style inputs */
  input[type=text]#logEntryWide,
  input[type=number]#pace-calc-time-input,
  textarea {
    font-size: 16px;
    text-align: left;
    width: 90%;
    resize: none;
    padding: 4px 4px;
    margin: 4px 4px;
    display: inline-block;
    border: 1px solid #ccc;
    border-radius: 3px;
    box-sizing: border-box;
  }

  input[type=number]::-webkit-inner-spin-button,
  input[type=number]::-webkit-outer-spin-button {
    -webkit-appearance: none;
    margin: 0;
  }

  /* Add a background color to the submit button on mouse-over */
  button:hover {
    background-color: #45a049;
  }

  div#minititle,
  caption {
    color: white;
    text-align: center;
    border: outset;
    border-width: 5px;
    font-size: 32px;
    font-weight: 100;
    background-color: var(--primary);
    margin: 0;
    padding: 0;
  }

  .card {
    background-color: rgb(204, 204, 204);
    transition: 0.3s;
    margin-bottom: 20px;

  }

  /* On mouse-over, add a deeper shadow */
  .card:hover {
    background-color: rgb(222, 222, 222);
    box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.2);
  }

  #pace-c,
  #log-e {
    min-width: 280px;
  }

  #daily-hab {
  }

  :root {
  --primary: rgb(66, 78, 105);
  --secondary: rgb(66, 78, 105);
  --tertiary: rgb(66, 78, 105);
}
</style>