<template>
    <div id='pace-calculator'>
        <table id="paceCalcTable">
            <tbody>
                <tr>
                    <td>
                        Time
                    </td>
                    <td>
                        <input id="pace-calc-time-input" type="number" placeholder="Hrs" maxlength="2" v-model="timehr">
                    </td>
                    <td>
                        <input id="pace-calc-time-input" type="number" placeholder="Min" maxlength="2"
                            v-model="timemin">
                    </td>
                    <td>
                        <input id="pace-calc-time-input" type="number" placeholder="Sec" maxlength="3"
                            v-model="timesec">
                    </td>
                </tr>
                <tr>
                    <td>
                        Distance
                    </td>
                    <td>
                        <input type="radio" name="units" value="mile" checked v-model="units"
                            v-on:change="changeDistance">mile<br>
                        <input type="radio" name="units" value="km" checked v-model="units"
                            v-on:change="changeDistance">km<br>
                    </td>
                    <td colspan="2">
                        <input id="pace-calc-time-input" type="number" placeholder="0" v-model="pcdist">
                    </td>
                </tr>
                <tr>
                    <td>
                        Pace per {{units}}
                    </td>
                    <td colspan="2">
                        {{pace}}
                    </td>
                    <td>
                        <button id="gridbutton" v-on:click="resetPaceCalc">Reset</button>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
    export default {
        name: 'pace-calculator',
        data() {
            return {
                timehr: null,
                timemin: null,
                timesec: null,
                pcdist: null,
                units: "mile"
            }
        },
        methods: {
            changeDistance: function () {
                if (this.pcdist != null) {
                    if (this.units == "mile") {
                        this.pcdist = this.fixRoundingError(this.pcdist * 0.621371);
                    } else {
                        this.pcdist = this.fixRoundingError(this.pcdist * 1.60934);
                    }
                }
            },
            fixRoundingError: function (val) {
                if(Math.abs(val % 1) > .99)
                {
                    return Math.round(val)
                }
                else
                {
                    return val;
                }
            },
            resetPaceCalc: function () {
                this.timehr = this.timemin = this.timesec = null;
                this.pcdist = '';
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
            }

        },
        computed: {
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

<style scoped>
    button#gridbutton {
        font-size: 16;
        width: 80%;
        color: black;
        padding: 6px 7px;
        margin: 8px 0;
        border: none;
        border-radius: 4px;
        cursor: pointer;
    }

    #pace-calculator {
        width: 90%;
        margin: 0 5%;
    }
</style>