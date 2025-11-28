

import {users_store} from "$lib/user";
let users = [];




<script>
let color ="Black"
let user = ""
let colors = [
    {namn: "Svart", value: "Black"},
    {namn: "Röd", value: "Red"},
    {namn: "Blå", value: "Blue"},
    {namn: "Grön", value: "Green"},
    {namn: "Gul", value: "Yellow"},
    {namn: "Lila", value: "Purple"},
    {namn: "Orange", value: "Orange"},
]
function handleSubmit(){

}

</script>



<main>

<div

    class ="container" >
    <h1>register</h1>
<form on:submit|preventDefault={handleSubmit}>
<div style="width: 100px; height: 100px; border-radius: 50%; overflow:hidden; background-color:{color};"></div>
    
<label for="name">name:</label>
    <input type="text" id="name" bind:value={user} >
<br>
<label for="name">email:</label>
    <input type="email" id="email" >
<br>
<label for="PASSWORD">password:</label>
    <input type="password" id="password" >
<br>
<label for="name">välj färg:</label>
<select bind:value={color}>
{#each colors as c}
<option value={c.value}>{c.namn}</option>
{/each}

</select>
<br>

<input type="submit" value="Register">

    



</form>

</div>
</main>

<style>
 main{
        background-image: url("https://t4.ftcdn.net/jpg/05/21/65/59/360_F_521655929_N80d5GaCQJ2VP073PfTXJTe9mkvsNtHE.jpg");
        background-size: cover;
        width: 100%;
        height: 100%;
        padding: 5%;

    }
    .container{
border: solid 5px rosybrown;
        border-radius: 10px;
        width: 35%;
        height: 80%;
        background-color: #3a2e3b;
        margin: auto;
        min-width: 300px;
        min-height: 500px;

        
    }
    .container
    {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: space-evenly;
        
    }
  
        
</style>
