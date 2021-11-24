<template>
  <div
        class="sort-filter-mecha"
        v-bind:style="{ backgroundColor: backgroundColor, borderRadius: '8px', color: 'white' }"
  > 
    <b-row class="mt-3">
        <b-col md="8">
            <p><b>Total: 1466</b></p>
        </b-col>
        <b-col md="4">
            <p><u v-bind:style="{ color: 'blue' }">Clear</u></p>
        </b-col>
    </b-row>
    <b-row class="ml-3" v-bind:style="{ color: 'white' }">
        <h2>Race</h2>
    </b-row>
    
    <b-row class="" id="searchMecha">
        <b-form inline>
            <b-form-input size="sm" class="mr-sm-2" placeholder="Search"></b-form-input>
            <b-button size="sm" class="my-2 my-sm-0" type="submit">Search</b-button>
        </b-form>

    </b-row>
    <b-row id="raceList">
        <b-col>
            <div v-for="(race, index) in races" :key="index">
                <input type="checkbox"> <img src="@/assets/alien1.png" alt="Races" id="imageRace">{{ race.race }}

            </div>
        </b-col>
    </b-row>

    <b-row class="ml-3" v-bind:style="{ color: 'white' }">
        <h2>Element</h2>
    </b-row>
    <b-row id="raceList">
        <b-col>
            <div v-for="(element, index) in elements" :key="index">
                <input type="checkbox"> <img src="@/assets/alien2.png" alt="Elements" id="imageElement">{{ element.element }}

            </div>
        </b-col>
    </b-row>
    <b-row class="ml-3" v-bind:style="{ color: 'white' }">
        <h2>Sale</h2>
    </b-row>
    <b-row>
        <b-col md="6">
            <input type="checkbox">Listed
        </b-col>
        <b-col md="6">
            <input type="checkbox">Unlisted
        </b-col>
    </b-row>
  </div>  
</template>

<script>
import axios from "axios"
export default {
    data() {
        return {
            backgroundColor: '#65A8FF',
            races: [
                { race: "Legion", value: false },
                { race: "Ravager", value: false },
                { race: "Giant", value: false },
                { race: "Aerial", value: false },
                { race: "Alien", value: false },
                { race: "Relic", value: false },
                { race: "Shapeshifter", value: false },
            ],
            elements:[
                { element: "Fire", value: false },
                { element: "Ice", value: false },
                { element: "Thunder", value: false },
                { element: "Earth", value: false },
                { element: "Air", value: false },
                { element: "Water", value: false },
                { element: "Light", value: false },
                { element: "Dark", value: false },
            ]
        }
    },
    async mounted() {
        let API_URL = "http://localhost:8000/subgraphs/name/mechmasterstudio/marketgraph"
        let result = await axios.post(API_URL, {
            query: `query Query {
                tokens {
                    id
                    tokenID
                }
            }`
        });
        console.log(result.data.data.tokens);
        let Ndata = result.data.data.tokens.length;
    }
}
</script>

<style>
#sort-filter-mecha {
    background-color: 8383FF;
    color: blue;
}
p {
    color: white;
}

#searchMecha {
    text-align: center;
    margin-left: 10px;
}

#raceList {
    text-align: left;
    margin-left: 10px;
}

#imageRace, #imageElement {
    width: 15px;
    height: 15px;
}
</style>