
<template>
  <section id="property-list">
    <div id="product-list-head">
      <p id="search-message">
        Nós encontramos <span id="results-num">{{Object.keys(cardApiData).length}}</span> Imoveis disponiveis !!
      </p>
      <button id="filter-button">Filtros</button>
    </div>

    <div id="card-list-container">
        <propertyCard 
            v-for="(card, index) in cardApiData" 
            :key="index" 
            :cardData="card"
            @card_clicked="cardShowOverview"
        />
    </div>
    <propertyOverview v-if="showOverview"/>
  </section>
</template>

<script setup>
import propertyCard from "@/components/propertyCard.vue";
import propertyOverview from "@/components/propertyOverview";

import { onBeforeMount, onMounted, ref } from "vue";

const cardApiData = ref({});
const showOverview = ref(false);

const api_url = "http://localhost:8080/geoplace/api/properties";

onBeforeMount(async ()=>{
    const response = await fetch(api_url);
    if (response.ok) {
        cardApiData.value = await response.json();
    }
})

function cardShowOverview(card_id) {
   let card_list_container = document.getElementById("card-list-container");
   card_list_container.style.width = "45%";
   card_list_container.style.margin = "0 0";
   card_list_container.style.transition = "0.5s";
   showOverview.value = true;
}

</script>

<style scoped>
#property-list {
    display: flex;
    flex-wrap: wrap;
    background-color: gainsboro;
    width: min(var(--min-width), var(--max-with));
    margin: 10px 5px;
    padding: 4px 10px;
}

#product-list-head {
    width: 100%;
    display: grid;
    grid-template-columns: 50% 50%;
    background-color: antiquewhite;
}

#card-list-container {
    width: 100%;
    margin: auto auto;
    display: flex;
    height: 90vh;
    flex-wrap: wrap;
    justify-content: flex-start;
    gap: 2%;
    overflow: auto;
}

    #search-message {}
    #results-num {font-weight: 900;}

    #filter-button {
        margin-left: auto;
        background: url("@/assets/icons/filter_icon.svg") no-repeat 2% center / 27px;
        background-color: white;
        padding: 10px;
        border-radius: 5px;
        text-align: right;
        width: 20%;
        border: none;
        outline: none;
        cursor: pointer;
    }
</style>