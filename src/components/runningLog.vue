<template>
    <div id="running-log">
        <table id="secondTable">
            <tr>
                <th id="table-id"> ID </th>
                <th id="table-date"> Date </th>
                <th id="table-distance"> Distance </th>
                <th id="table-time"> Time </th>
                <th id="table-distance"> Pace </th>
                <th id="table-notes"> Notes </th>
            </tr>
            <tbody>
                <tr v-for="(row,index) in rows" :key="index">
                    <td v-for="col in columns" :key="col.id">{{row[col]}}</td>
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
                        Date: "2020-02-14",
                        Distance: 6,
                        Time: "0:36:30",
                        Pace: "6:05.01",
                        Notes: "The run went well. Legs were a little sore."
                    },
                    {
                        id: 1,
                        Date: "2020-02-14",
                        Distance: 9.6,
                        Time: "1:09:36",
                        Pace: "7:15.00",
                        Notes: "Medium long run, was rather run to get to go a little farther than usual."
                    },
                    {
                        id: 2,
                        Date: "2020-02-14",
                        Distance: 7,
                        Time: "0:34:25",
                        Pace: "4:55.00",
                        Notes: "Shoutout to Sam for rescuing me. Felt super tired all day today even though I got really good sleep. Joyce thinks I should go get a physical to find out why I’ve been feeling fatigued. I think it’s probably iron deficiency bc of how shit my diet was at school. Starting taking iron supplements again so I’m gonna give it a few days. Felt really tired all day but I needed to force myself to run. Wanted to get out the stationary bike but it’s broke. Samantha swooped in time my rescue and bike beside me for this run. Running alone just sucks lately, haven’t been in the mood for it I guess. Started off slow but actually felt really good today so I definitely think running with people will help me feel good. Gonna have Sam do this more often too provided that she’s willing. Hopefully she can coach me through a tempo."
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

<style scoped>
    th,
    td {
        table-layout: fixed;
        font-size: 24px;
        border: 2px solid black;
        padding: 2px;
        align-self: center;
    }

    th {
        position: sticky;
        top: 0;
        z-index: 10;
        border: 4px;
    }

    table#secondTable {
        background-color:grey;
        border-collapse: collapse;
        display: block;
        overflow-y: scroll;
        overflow-x: hidden;
        table-layout: fixed;
        height: 500px;
        width: 100%;
    }

    table#secondTable tr:nth-child(even) {
        background-color: rgb(199, 215, 247);
    }

    table#secondTable tr:nth-child(odd) {
        background-color: rgb(158, 162, 207);
    }

    table#secondTable th {
        text-align: center;
    }
</style>