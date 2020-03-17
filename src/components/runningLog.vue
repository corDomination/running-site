<template>
    <div id="running-log">
        <table id="secondTable">
            <tr>
                <th v-for="col in columns" v-bind:key="col.id">{{col}} </th>
            </tr>
            <tbody>
                <tr v-for="(row,index) in rows" :key="index">
                    <td v-for="col in columns" v-bind:key="col.id">{{row[col]}}</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
    export default {
        name: 'running-log',
        props: [],
        data() {
            return {
                rows: [{
                        id: 0,
                        Date: "Fri Jan 24 2020 08:56:32 GMT-0500 (Eastern Standard Time)",
                        Distance: 6,
                        Time: "0:36:30",
                        Pace: "6:05.01",
                        Notes: "The run went well. Legs were a little sore."
                    },
                    {
                        id: 1,
                        Date: "Fri Jan 24 2020 08:56:32 GMT-0500 (Eastern Standard Time)",
                        Distance: 9.6,
                        Time: "1:09:36",
                        Pace: "7:15.00",
                        Notes: "Medium long run, was rather run to get to go a little farther than usual."
                    },
                    {
                        id: 2,
                        Date: "Fri Jan 24 2020 08:56:32 GMT-0500 (Eastern Standard Time)",
                        Distance: 7,
                        Time: "0:34:25",
                        Pace: "4:55.00",
                        Notes: "Tomorrow will be better."
                    }
                ]
            }
        },
        computed: {
            "columns": function columns() {
                if (this.rows.length == 0) {
                    return [];
                }
                return Object.keys(this.rows[0])
            }
        }
    }
</script>