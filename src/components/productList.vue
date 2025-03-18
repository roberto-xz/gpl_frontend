
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
    <propertyOverview 
        v-if="showOverview" 
        @close_overview="cardHiddenOverview"
        :cardData = "card"
    />
  </section>
</template>

<script setup>
import propertyCard from "@/components/propertyCard.vue";
import propertyOverview from "@/components/propertyOverview";

import { onBeforeMount, onMounted, ref } from "vue";

const cardApiData = ref({});
const card = ref({});

const showOverview = ref(false);

const api_url = "http://localhost:8080/geoplace/api/properties";

// apenas para debug
const fake_data = {
            d: Math.random()*100,
            title: "Property Not Found",
            address: "unknow-adress",
            cover: "property_default_image.jpg",
            price: "R$ 10.000,23",
            isFavorited: false,
            rooms: 3,
            bedrooms: 3,
            bathrooms: 3,
            kitchens: 3
        }
cardApiData.value = [
    fake_data,
    fake_data,
    fake_data,
    fake_data,
    fake_data,
    fake_data,
];
////////
onBeforeMount(async ()=>{
    const response = await fetch(api_url);
    if (response.ok) {
        cardApiData.value = await response.json();
    }
})

async function cardShowOverview(card_id) {
    const response = await fetch(`http://localhost:8080/geoplace/api/property/${card_id}`);
    if (response.ok) {
        card.value = await response.json();
        let card_list_container = document.getElementById("card-list-container");
        card_list_container.style.display = "none"
        card_list_container.style.margin = "0 0";
        card_list_container.style.transition = "0.5s";
        showOverview.value = true;
    }
}

function cardHiddenOverview() {
   let card_list_container = document.getElementById("card-list-container");
   card_list_container.style.display = "flex";
   card_list_container.style.margin = "auto auto";
   card_list_container.style.transition = "0.5s";
   showOverview.value = false;
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
    height: 20px;
}

#card-list-container {
    width: 90%;
    margin: auto auto;
    display: flex;
    height: 90vh;
    flex-wrap: wrap;
    justify-content: flex-start;
    gap: 2%;
    overflow: auto;
}

    #search-message {
        display: block;
        width: 100%;
        height: 15px;
    }
    #results-num {font-weight: 900;}

    #filter-button {
        margin-left: auto;
        background: url("@/assets/icons/filter_icon.svg") no-repeat 2% center / 27px;
        background-color: white;
        padding: 10px;
        border-radius: 5px;
        text-align: right;
        width: 20%;
        height: 15px;
        border: none;
        outline: none;
        cursor: pointer;
    }
</style>