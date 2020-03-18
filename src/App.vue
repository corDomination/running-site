<template>
  <div id="webpage">
    <top-bar>Jack's Running Site</top-bar>

    <body>
      <div class="leftcolumn">
        <div class="card">
            <div id="minititle">Running Log</div>
            <running-log></running-log>
        </div>
        <div class="card">
            <div id="minititle">Daily Habits</div>
            <daily-habits></daily-habits>
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
    </body>
  </div>
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
      return {
      }
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
    font-family: Helvetica, Arial, sans-serif;
    font-weight: 700;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }

  html {
    min-width: 1000px;
  }

  body {
    margin: 0;
    text-align: center;
    background: black;
    /* background: linear-gradient(90deg, rgba(2,0,36,0.7959558823529411) 10%, rgba(9,47,121,0.9220063025210083) 51%, rgba(8,10,14,0.7903536414565826) 100%); */
  }

  .leftcolumn {
    background-color: black;
    float: left;
    width: 65%;
    padding-left: 5%;
  }

  .rightcolumn {
    background-color: black;
    width: 25%;
    padding-right: 5%;
    float: left;
  }

  .row:after {
    content: "";
    display: table;
    clear: both;
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
    color: rgb(63, 71, 138);
    font-size: 36px;
    font-weight: 900;
    background-color: white;
    width: 100%;
  }

  .card {
    background-color: rgb(143, 132, 132);
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
    transition: 0.3s;
    margin: 12px 4px;
    width: 98%;
  }

  /* On mouse-over, add a deeper shadow */
  .card:hover {
    box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.2);
  }
  #pace-c {
    max-width: 300px;
  }
  #log-e {
    max-width: 300px;
  }
</style>