
<template>
    <article id="card-propertyCard">
       <img 
            @click="handleClick(cardData.id)"
            :src="'img/properties/'+cardData.cover" 
            class="property-cover" 
            alt=""
        />

        <div class="property-details">
            <p class="property-title"> 
                {{cardData.title}}
                {{cardData.id}}
                <span class="property-price"> {{cardData.price}} </span>
            </p>
            <p class="property-location"> {{cardData.address}}</p>
        </div>

        <ul class="property-amenities">
            <li class="amenities" title="Salas">
                <img src="img/icons/room.svg" alt="" class="amenitie-icon"/>
                <p class="amenitie-qtd">{{cardData.rooms}}</p>
            </li>
            <li class="amenities" title="Banheiros">
                <img src="img/icons/bathroom.svg" alt="" class="amenitie-icon"/>
                <p class="amenitie-qtd">{{cardData.bathrooms}}</p>
            </li>
            <li class="amenities" title="Quartos">
                <img src="img/icons/bedroom.svg" alt="" class="amenitie-icon"/>
                <p class="amenitie-qtd">{{cardData.bedrooms}}</p>
            </li>
            <li class="amenities" title="Cozinhas">
                <img src="img/icons/kitchen.svg" alt="" class="amenitie-icon"/>
                <p class="amenitie-qtd">{{cardData.kitchens}}</p>
            </li>
        </ul>
        <div class="favorited-box">
            <img src="img/icons/favorite.svg" alt="" class="amenitie-favorite-icon"/>
        </div>
    </article>
</template>

<script setup>
    defineProps({cardData: Object});
    const emit = defineEmits(["card_clicked"]);

    function handleClick(card_id) {
        emit("card_clicked",card_id);
    }
</script>

<style scoped>

article {
    position: relative;
    background-color:  rgb(255, 255, 255);
    width: 310px;
    margin: 10px 5px;
    cursor: pointer;
    border-radius: 5px 5px 0 0;
    padding-bottom: 10px;
}

.property-cover {
    display: block;
    width: 100%;
    border-radius: 5px;
}

.property-details { 
    display: block;
    width: 100%;
    border: 1px solid red;
    padding: 0 6px;
    margin: 20px 0;
}
.property-price {
    float: right;
    border: 1px solid green;
}

.property-location {
    font: 200 .9rem/1 Sans-serif;
    margin-top: 6px;
}

.property-amenities {
    display: flex;
    width: 100%;
    padding: 0 6px;
    list-style: none;
}

.amenities {
    display: grid;
    grid-template-columns: 50% 50%;
    background-color: white;
    border: 1px solid #000;
    width: 70px;
    padding: 2px;
    border-radius: 5px;
    margin-right: 10px;
}

.favorited-box {
    position: absolute;
    display: flex;
    justify-content: center;
    align-items: center;
    left: 85%; top: 3%;
    width: 34px;
    height: 34px;
    background-color: whitesmoke;
    border-radius: 100%;
}

.favorited-box:hover {
    background-color: gray;
}

.amenitie-favorite-icon {width: 70%;}


</style>