<script setup>
import {ref, reactive} from 'vue'
import {DatePicker } from 'v-calendar'
import 'v-calendar/dist/style.css'

const date = ref(new Date())
date.value.setDate(Number(date.value))
const range= reactive({
    start: new Date(),
    end:new Date(),
    end:date.value
})
</script>

<template>
    <DatePicker v-model="date" mode="dateTime" 
    :columns="2" is-range
    >
    <template v-slot="{inputValue, inputEvents}">
     <div class="group">
    <label class="button groupItem" for="start">Start</label>
    <input type="text" id="start" 
     :value="inputValue.start"
    v-on="inputEvents.start" class="input groupItem"/>
    <label class="button groupItem" for="end">End</label>
    <input type="text" id="end" for="end"
    :value="inputValue.end"
   readonly
     class="input groupItem"/>
     </div>
    
    </template>
    
    </DatePicker>

<p>
 Date:{{date.toJSON()}}
</p>
</template>
<style scoped>
@use form{
    field:label, group,input, button;
}
</style>