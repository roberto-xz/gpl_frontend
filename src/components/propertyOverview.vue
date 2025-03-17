
<template>
    <section id="propery-overview">
        <button id="close-overview-bnt">x</button>
        <div id="overview-container">
            <img src="img/defaults/property_default_image.jpg" id="zoom-image" alt=""/>
                <div id="small-images-container">
                    <img src="" class="small-image" alt=""/>
                    <img src="" class="small-image" alt=""/>
                    <img src="" class="small-image" alt=""/>
                    <img src="" class="small-image" alt=""/>
                </div>
          
            <div id="porperty-about">
                <div>
                    <h1>Casa para vender</h1>
                    <p id="property-location">Petrolina-PE</p>
                </div>
                <span id="price">R$ 56, 9000</span>
                <span id="contract-type">Aluguel</span>
                <h1>Descrição</h1>
                <p id="description"></p>
                <h3>Caracteristicas</h3>
                <ul class="property-amenities">
                    <li class="amenities" title="Salas">
                        <img src="img/icons/room.svg" alt="" class="amenitie-icon"/>
                        <p class="amenitie-qtd">5</p>
                    </li>
                </ul>
            </div>
            <div id="contact-container">
                <div id="user-infos">
                    <img src="" alt="" id="user-profile"/>
                    <p>
                        <span>User-name</span>                        
                        <span>User-UUID</span>                        
                    </p>
                </div>
                <button>Mandar mensagem</button>
            </div>
        </div>
    </section>
</template>

<style scoped>

#propery-overview {
    display: flex;
    flex-wrap: wrap;
    justify-content: flex-start;
    align-items: flex-start;
    background-color: rgb(255, 252, 252);
    flex: 1;
    margin: 10px 5px;
    padding: 4px 10px;
    border: 1px solid red;
    border-radius: 10px;
}

#close-overview-bnt {
    display: block;
    width: 100%;
    height: 20px;
    background: none;
    border: 1px solid red;
    outline: none;
    text-align: right;
}
</style>