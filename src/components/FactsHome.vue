<template>
    <div>
        <h2>facts:</h2>
        <li v-for="fact in facts" :key="fact">
            {{fact.details}}
        </li>
        <div>
            <label>Fact details:</label>
             <input v-model="data.details" type="text" >
        </div>
        <button @click="createFact">Create a Fact!</button>
    </div>

</template>

<script>
import { reactive, ref } from '@vue/reactivity'
import { onMounted } from '@vue/runtime-core'
export default {
    name: 'FactsHome',
    setup(){
        let facts = ref([])
        let data = reactive({
            details: ''
        })

        onMounted(async () => {
            const response = await fetch('http://localhost:8000/api/facts/getfacts',{
            headers: {'Content-Type': 'application/json'}
            })

            const content = await response.json()
            facts.value = content;
            console.log(facts.value)
        })

        const createFact = async () => {
            console.log(data)
            await fetch('http://localhost:8000/api/facts/create',{
                method: 'POST',
                headers: {'Content-Type': 'application/json'},
                body: JSON.stringify(data)
            });
        }

        return {
            facts,
            data,
            createFact
        }
    }
}
</script>

<style>

</style>