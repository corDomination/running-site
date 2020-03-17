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
                        <input type="radio" name="units" value="mile" checked v-model="units">mile<br>
                        <input type="radio" name="units" value="km" checked v-model="units">km<br>
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
                units: "mile"
            }
        },
        methods: {
            resetPaceCalc: function () {
                this.timehr = this.timemin = this.timesec = null;
                this.pcdist = '';
            }
        }
    }
</script>