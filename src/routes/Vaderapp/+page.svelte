<script>
  import { onMount } from "svelte";

  let weather = null;
    let temps
    let temps_tomorrow
    let uv 
    let uv_tomorrow
    let rain = 0;
    let rain_tomorrow = 0;
    let time
    let tempsF
    let tempsK
    let tempsF_tomorrow
    let tempsK_tomorrow
  onMount(async () => {
    const res = await fetch("https://api.open-meteo.com/v1/forecast?latitude=63.7918&longitude=20.2828&daily=uv_index_max&hourly=temperature_2m,rain&timezone=Europe%2FBerlin&forecast_days=3");
    weather = await res.json();
    temps = weather.hourly.temperature_2m[12]
    temps_tomorrow = weather.hourly.temperature_2m[36]
    uv = weather.daily.uv_index_max[0]
    uv_tomorrow = weather.daily.uv_index_max[1]
    
    for (let i = 0; i < 23; i++) {
        rain += weather.hourly.rain[i];
    }

    for (let i = 24; i < 48; i++) {
        rain_tomorrow += weather.hourly.rain[i];
    }

    tempsF = (temps * (9/5) + 32).toFixed(1)
    tempsK = (temps + 273.15).toFixed(1)
    tempsF_tomorrow = (temps_tomorrow * (9/5) + 32).toFixed(1)
    tempsK_tomorrow = (temps_tomorrow + 273.15).toFixed(1)

    





    });
</script>
    <h1>Väder i umeå</h1>


<main>

    <div class = ruta1>
        <h2> Idag kl:12 </h2> 
        <h3>Tempratur</h3>
        {temps} C°
        <h3> </h3>
        {tempsF} F°
        <h3> </h3>
        {tempsK} K°
        {#if tempsK < 200}
        <h3>Gå inte ut!</h3>
        {:else if tempsK > 360}
        <h3>Gå inte ut!</h3>
        {:else}
        <h3>Okej att gå ut</h3>
        {/if}
        <h3>Uv</h3>
        {uv}
        {#if uv < 0}
        <h3>Gå inte ut!</h3>
        {:else if uv > 10}
        <h3>Gå inte ut!</h3>
        {:else}
        <h3>Okej att gå ut</h3>
        {/if}
        <h3> aktulla regn prognosen </h3>
        {#if rain > 40}
            <h3>Regn idag</h3>
        {:else if rain > 30}
            <h4>varning varning gå inte ut varning varning detta är en varning</h4>
        {:else if rain > 20}
            <h4>kan vara farligt att gå ut</h4>
        {:else if rain > 10}
            <h4>var inte ute för länge</h4>
        
        {:else if rain > 0}
            <h4>det är lugnt att gå ut</h4>
        {:else}
            <h4>Inget regn idag</h4>
        {/if}
       
    </div>
    <div class = ruta2>
        <h2> Imorgon kl: 12 </h2>
        <h3>Tempratur</h3>
        {temps_tomorrow} C°
        <h3> </h3>
        {tempsF_tomorrow} F°
        <h3> </h3>
        {tempsK_tomorrow} K°
        {#if tempsK_tomorrow < 200}
        <h3>Gå inte ut!</h3>
        {:else if tempsK_tomorrow > 360}
        <h3>Gå inte ut!</h3>
        {:else}
        <h3>Okej att gå ut</h3>
        {/if}
        <h3>Uv</h3>
        {uv_tomorrow}
        {#if uv_tomorrow < 0}
        <h3>Gå inte ut!</h3>
        {:else if uv_tomorrow > 10}
        <h3>Gå inte ut!</h3>
        {:else}
        <h3>Okej att gå ut</h3>
        {/if}
         <h3> regn prognosen </h3>
        {#if rain_tomorrow > 40}
            <h3>Regn idag</h3>
        {:else if rain_tomorrow > 30}
            <h4>varning varning gå inte ut varning varning detta är en varning</h4>
        {:else if rain_tomorrow > 20}
            <h4>kan vara farligt att gå ut</h4>
        {:else if rain_tomorrow > 10}
            <h4>var inte ute för länge</h4>
        {:else if rain_tomorrow > 0}
            <h4>det är lugnt att gå ut</h4>
        {:else}
            <h4>Inget regn imorgon</h4>
        {/if}
        
        

         
    </div>
    


</main>
<style>
    main{
        display:flex;
        flex-wrap:nowrap;
        justify-content: center;
    }
    h1{
        color:black;
        text-align:center;
    }
    h2{
        text-align: center;
    }
    .ruta1{
        display:flex;
        height:40%;
        width:40%;
        border: 2px solid black;
        margin-top:75px;
        margin-right:35px;
        background:lightskyblue;
        flex-direction:column;
        text-align: center;
    }
    .ruta2{
        display:flex;
        height:40%;
        width:40%;
        border: 2px solid black;
        margin-top:75px;
        margin-left:35px;
        background:lightskyblue;
        flex-direction:column;
        text-align: center;
    }
</style>

