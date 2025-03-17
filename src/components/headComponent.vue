
<template>
    <header>
        <img id="geoplace-logo-img" alt="" src="@/assets/text_logo.svg"/>
        <div id="property-types-options">
            <label>Comprar  <input type="radio" name="property-type" value="buy"/></label>
            <label>Alugar   <input type="radio" name="property-type" value="rent"/></label>
            <label>Anunciar <input type="radio" name="property-type" value="sell"/></label>            
            <label>Favoritos<input type="radio" name="property-type" value="favs"/></label>            
        </div>

        <input type="text"   id="search-input" placeholder="Procurar imóveis .."/>
        
        <div id="user-perfil-box">
            <img id="user-messagens-bnt" alt="" src="@/assets/icons/chat_icon.svg"/>
            <img id="user-profile-img" alt="" src="@/assets/defaults/user_profile.png"/>
            <div id="user-ids-box">
                <span id="user-name">user-name-teste</span>
                <span id="user-uuid">user-uuid-teste</span>
            </div>
        </div>
    </header>
</template>

<style scoped>

input[type="radio"] {display: none;}

header {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
    width: min(var(--min-width), var(--max-with));
    outline: 1px solid red;
}

#geoplace-logo-img {
    display: block;
    width: 100px;
}
#property-types-options {
    display: flex;
    width: auto;
    background-color: rgb(166, 171, 244);
    border-radius: 20px;
    margin-left: 10%;
}

#property-types-options  label {
    padding: 5px;
    margin: 5px;
    cursor: pointer;
}

#search-input {
    width: 20%;
    margin: 0 4%;
    padding: 10px;
    border-radius: 10px;
    border: 1px solid #000;
    background: url('@/assets/icons/lupe_icon.svg') no-repeat 2% center / 27px;
    padding-left: 40px;
}

#user-perfil-box {
    display: grid;
    align-items: center;
    grid-template-columns: 10% 30% 60%;
    width: 400px;
    border: 1px solid green;
}
#user-messagens-bnt {
    width: 25px;
    margin: auto auto;
}
#user-profile-img {
    width: 56px;
    border: 1px solid #000;
    border-radius: 100%;
    margin-left: auto;
}

#user-ids-box {display: block;}
#user-ids-box span {
    display: block;
    margin-left: 10px;
    border: 1px solid red;    
}

#user-ids-box span:first-child {
    font-weight: 900;
}

</style>>