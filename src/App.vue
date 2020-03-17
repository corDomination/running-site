<template>
  <div id="webpage">
    <top-bar>Jack's Running Site</top-bar>

    <body>
      <div class="leftcolumn">
        <div class="card">
          <div class="container">
            <running-log></running-log>
          </div>
        </div>
        <div class="card">
          <div class="container">
            <div id="minititle">Daily Habits</div>
            <daily-habits></daily-habits>
          </div>
        </div>
        <div class="card">
          <div class="container">
            <div id="minititle">Pace Calculator</div>
            <pace-calculator></pace-calculator>
          </div>
        </div>
      </div>
      <div class='rightcolumn'>
        <div class="card">
          <div class="container">
            <div id="minititle">Log Entry</div>
            <new-log-entry></new-log-entry>
          </div>
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
    el: '#webpage',
    data() {
      return {
        newTimehr: null,
        newTimemin: null,
        newTimesec: null,
        pcdist: null,
        newDistance: null,
        newTime: '',
        newItem: '',
        currHeadID: 2,
      }
    },
    methods: {
      saveItem: function () {
        if (this.newDistance != '') {
          if (this.newTimehr != null || this.newTimemin != null || this.newTimesec != null) {
            if (this.newTimehr == null) {
              this.newTimehr = 0;
            }
            if (this.newTimemin == null) {
              this.newTimemin = 0;
            }
            if (this.newTimesec == null) {
              this.newTimesec = 0;
            }
            var t = this.newTimehr.toString() + ":" + this.addZerosIf(this.newTimemin.toString(), 1) + ":" + this
              .addZerosIf(this.newTimesec.toString(), 1);
            var s = this.calcTotalSeconds(this.newTimehr, this.newTimemin, this.newTimesec);
            var pac = this.calculatePace(s, this.newDistance);
            this.currHeadID += 1
            this.rows.push({
              id: this.currHeadID,
              Date: new Date(),
              Distance: this.newDistance,
              Time: t,
              Pace: pac,
              Notes: this.newItem
            });
            this.newItem = this.newDistance = '';
            this.newTimehr = this.newTimemin = this.newTimesec = null;
          }
        }
      },
      addTestItem: function () {
        this.currHeadID += 1
        this.rows.push({
          id: this.currHeadID,
          Date: new Date(),
          Distance: 4,
          Time: "20:20",
          Pace: "5:05",
          Notes: "Test"
        });
      },
      calculatePace: function (totsec, di) {
        var pacestring = "";
        totsec = (totsec / (Number(di)));
        totsec = totsec % 3600.0;
        pacestring += (Math.floor(totsec / 60.0)).toString();
        pacestring += ":";
        var z = (totsec % 60.0).toFixed(2);
        if (z.length == 4) {
          pacestring += '0';
        }
        pacestring += z.toString();
        return pacestring;
      },

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
      },
      addZerosIf: function (str, val) {
        if (str.length == val) {
          return str = '0' + str;
        } else {
          return str;
        }
      }
    },
    computed: {
      "weekMileage": function weeksMiles() {
        var weeklyMileage = 0;
        for (var i = this.rows.length; i > 0; i--) {
          weeklyMileage += this.rows[i].Distance;
        }
        return weeklyMileage;
      },
      "pace": function calcpace() {
        var totalsecs = this.calcTotalSeconds(this.timehr, this.timemin, this.timesec);
        var d = this.pcdist;
        if (totalsecs == 0) {
          return "Enter a time";
        }

        if (d == null) {
          return "Enter a distance";
        }
        var p = this.calculatePace(totalsecs, d);
        if (p[0] == 'N') {
          return "";
        }
        return p;
      }
    }
  }
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }

  p#menutitle {
    float: left;
    width: 100%;
    margin: 8px 0;
    border: none;
    font-size: 64px;
    text-align: center;
    color: white;
    background-color: black;

  }

  html {
    background-color: black;
    min-width: 1000px;
  }

  body {
    margin: 0;
    text-align: center;
    background: none;
    /* background: linear-gradient(90deg, rgba(2,0,36,0.7959558823529411) 10%, rgba(9,47,121,0.9220063025210083) 51%, rgba(8,10,14,0.7903536414565826) 100%); */
  }

  .leftcolumn {
    float: left;
    width: 50%;
  }

  .rightcolumn {
    width: 50%;
    float: left;
  }

  .row:after {
    content: "";
    display: table;
    clear: both;
  }

  a {
    font-size: 30px;
    color: white;
    text-decoration: none;
    border-radius: 6px;
    border: 4px solid white;
    margin: 8px;
  }

  nav {
    color: whitesmoke;
    text-align: center;
    font-size: 48px;
    font-family: "Courier New", Courier, monospace;
    background-color: black;
    width: 100%;
    border-top: 10px solid red;
    border-bottom: 10px solid red;
  }

  th,
  td {
    table-layout: fixed;
    font-size: 20px;
    text-align: center;
    border: 2px solid black;
    padding: 15px;
    align-self: center;
  }

  th {
    position: sticky;
    top: 0;
    z-index: 10;
    border: 4px;
  }

  table#secondTable {
    background-color: white;
    display: block;
    overflow-y: scroll;
    overflow-x: hidden;
    table-layout: fixed;
    height: 500px;
    width: 100%;
  }

  table#secondTable tr:nth-child(even) {
    background-color: rgb(250, 221, 221);
  }

  table#secondTable tr:nth-child(odd) {
    background-color: rgb(248, 190, 190);
  }

  table#secondTable th {
    color: white;
    background-color: black;
  }



  /* Style inputs */
  input[type=text]#logEntryWide,
  input[type=number]#pace-calc-time-input,
  textarea {
    font-size: 20px;
    text-align: left;
    width: 90%;
    padding: 12px 20px;
    margin: 8px 0;
    display: inline-block;
    border: 1px solid #ccc;
    border-radius: 4px;
    box-sizing: border-box;
  }

  input[type=number]::-webkit-inner-spin-button,
  input[type=number]::-webkit-outer-spin-button {
    -webkit-appearance: none;
    margin: 0;
  }


  /* Style the submit button */
  button#biggerbutton {
    font-size: 24;
    width: 50%;
    color: black;
    padding: 14px 20px;
    margin: 8px 0;
    border: none;
    border-radius: 4px;
    border-color: #999;
    cursor: pointer;
  }

  button#gridbutton {
    font-size: 24;
    width: 80%;
    color: black;
    padding: 14px 20px;
    margin: 8px 0;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }

  /* Add a background color to the submit button on mouse-over */
  input[type=submit]:hover {
    background-color: #45a049;
  }

  table#paceCalcTable {
    background-color: grey;
    margin-top: 20px;
    float: right;
    table-layout: fixed;
    border: 2px solid black;
    border-collapse: collapse;
    width: 100%;
  }

  div#minititle,
  caption {
    color: red;
    font-size: 64;
    background-color: black;
    width: 100%;
  }

  input[type=number]#logEntrySmall {
    font-size: 20px;
    text-align: left;
    width: 29.4%;
    padding: 12px 20px;
    margin: 8px 0;
    display: inline-block;
    border: 1px solid #ccc;
    border-radius: 4px;
    box-sizing: border-box;
  }

  iframe {
    width: 100%;
    height: 400;
  }

  div#topbar {
    padding: 0px 0px;
  }

  ul {
    font-size: 32px;
    /*
  border-width: 6px 4px 6px 4px;
  border-style: outset;
  */
  }


  .card {

    background-color: rgb(143, 132, 132);
    /* Add shadows to create the "card" effect */
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
    transition: 0.3s;
    margin: 10%;
    width: 80%;
  }

  /* On mouse-over, add a deeper shadow */
  .card:hover {
    box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.2);
  }

  /* Add some padding inside the card container */
  .container {
    padding: 2px 16px;
  }
</style>