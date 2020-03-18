<template>
  <div id="new-log-entry">
    <br>
    <input id="logEntrySmall" type="number" placeholder="Hrs" maxlength="2" v-model="newTimehr">
    <input id="logEntrySmall" type="number" placeholder="Min" maxlength="2" v-model="newTimemin">
    <input id="logEntrySmall" type="number" placeholder="Sec" maxlength="3" v-model="newTimesec">
    <input id="logEntryWide" type="text" v-model="newDistance" placeholder="Distance">
    <textarea id="logEntryWide notes" type="text" v-model="newItem" placeholder="Notes" rows="5" cols="60"
      name="description"></textarea>
    <button id="biggerbutton" v-on:click="saveItem">Submit New Activity</button>
    <button id="biggerbutton" v-on:click="addTestItem">Add test item</button>
  </div>
</template>

<script>
  export default {
    name: 'new-log-entry',
    props: [],
    data () {
      return {
        newTimehr: null,
        newTimemin: null,
        newTimesec: null,
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
      addZerosIf: function (str, val) {
        if (str.length == val) {
          return str = '0' + str;
        } else {
          return str;
        }
      }
    }
  }
</script>

<style scoped>
  button#biggerbutton {
    font-weight: 500;
    width: 45%;
    color: black;
    padding: 6px 2px;
    margin: 8px 2px;
    border: none;
    border-radius: 4px;
    border-color: #999;
    cursor: pointer;
  }

  input[type=number]#logEntrySmall {
    font-size: 16px;
    text-align: left;
    width: 27.5%;
    padding: 4px 4px;
    margin: 4px 8px;
    display: inline-block;
    border: 1px solid #ccc;
    border-radius: 3px;
    box-sizing: border-box;
  }
</style>