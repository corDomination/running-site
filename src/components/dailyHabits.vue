<template>
    <div id="daily-habits">
        <br>
        <ul v-for="(item,index) in dailyMaxims" :key="index">
            {{item}}
        </ul>
    </div>
</template>

<script>
    export default {
        name: 'new-log-entry',
        props: [],
        data() {
            return {
                dailyMaxims: ["Train Smart", "Carbs and Protein focus", "Daily Recovery and Stretching",
                    "Physical Therapy",
                    "Supplemental strengthening exercises", "8 Hours of sleep"
                ]
            }
        }
    }
</script>