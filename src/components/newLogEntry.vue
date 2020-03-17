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
}
</script>