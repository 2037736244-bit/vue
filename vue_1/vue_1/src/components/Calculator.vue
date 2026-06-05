<template>
    <div class="person">
        <h2>🌡️ 温度转换器</h2>
        <div>
            <label for="celsius">摄氏度：</label>
            <input id="celsius" type="number"   v-model.number="celsius" />
            <span>{{celsiusToF}}°F</span>
        </div>
        <div>
            <label for="fahrenheit">华氏度：</label>
            <input id="fahrenheit" type="number" v-model.number="fahrenheit"/>
             <span>{{fahrenheitToC}}°F</span>
        </div>
        
    </div>
</template>

<script setup>
defineOptions({
    name: 'Calculator'
})
import { ref, computed } from 'vue'
const celsius = ref(0)
const fahrenheit = ref(32)
const celsiusToF = computed({
    get: () => (celsius.value * 9/5 + 32).toFixed(1),
    set: (val) => {
        celsius.value = ((val - 32) * 5/9).toFixed(1)
    }
})
const fahrenheitToC = computed({
  get: () => ((fahrenheit.value - 32) * 5/9).toFixed(1),
  set: (val) => {
    fahrenheit.value = (val * 9/5 + 32).toFixed(1)
  }
})

</script>

<style scoped>
.person {
    text-align: center;
    max-width: 400px;
    margin: 50px auto;
    font-family: sans-serif;
}   
</style>