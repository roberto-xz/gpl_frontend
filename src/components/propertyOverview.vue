
<template>
    <section id="propery-overview">
        <button id="close-overview-bnt" @click="emit('close_overview',0)">x</button>
        <div id="left-container">
            <img :src="'img/properties/'+cardData.cover" id="zoom-image" alt=""/>
            <div id="small-images-container">
                <img 
                    v-for="(img,index) in cardData.images" 
                    :key="index"
                    :src="'img/properties/'+img" class="small-image" alt=""
                    @click="upToZoom(img)"
                />
            </div>
        </div>
        
        <div id="right-container">
            <h1>
                {{cardData.title}}
                <p id="property-location">{{cardData.address}}</p>
                R$ {{cardData.price}}
            </h1>
            <h2>Decrição</h2>
            <p id="description">
                {{cardData.description}}
            </p>
            <h3>Caracteristicas</h3>
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
        </div>
    </section>
</template>

<script setup>
    const emit = defineEmits(["close_overview"]);
    const prop = defineProps({cardData:Object});

    function upToZoom(imgUrl) {
        document.getElementById("zoom-image").src = `img/properties/${imgUrl}`
    }
</script>


<style scoped>

#propery-overview {
    display: flex;
    position: relative;
    width: 100%;
    margin: 10px 5px;
    padding: 4px 10px;
    border: 1px solid red;
}

#left-container, #right-container {
    width: 50%;
    background-color: rgb(255, 252, 252);
    overflow: hidden;
    padding: 10px;
}

#close-overview-bnt {
    position: absolute;
    background: none;
    top: 0; left: 97%;
    display: block;
    width: 40px;
    height: 40px;
    outline: none;
    border: none;
    text-align: center;
    cursor: pointer;
}
#zoom-image {display: block;width: 100%;}
#small-images-container {
    width: 100%;
    display: grid;
    overflow: auto;
    grid-template-columns: repeat(4, 1fr);
}
    .small-image {
        display: block;
        width: 100%;
        cursor: pointer;
        padding: 10px;
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

</style>