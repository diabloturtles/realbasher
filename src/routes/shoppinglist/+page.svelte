
<script>
    let nyVara = $state("");
    let varor = $state([ { name: "placeholder", köpt: false } ]);
    

    function movevara(index) {
        varor[index].köpt = !varor[index].köpt;
    }
    function deletevara(index) {
        varor.splice(index, 1)
    }
</script>
<main class ="container">  
    <h1>shoppinglist</h1>
    <div class ="categories_container" >
        <section>
            <h2>merry christmas</h2>
            <ol>
                {#each varor as vara, index}
                {#if vara.köpt == false}
                <li>
                    { vara.name }
                    <button onclick={() => {movevara(index)}}>move</button>
                    <button onclick={() => {deletevara(index)}}>X</button>


                </li>
                {/if}
                {/each}
            </ol>
        </section>
        <section>
            
            <h2>merry christmas</h2>
            <ol>
                {#each varor as vara, index}
                {#if vara.köpt == true }
                <li>
                    { vara.name }
                    <button onclick={() => {movevara(index)}}>move</button>
                    <button onclick={() => {deletevara(index)}}>X</button>

                </li>
                {/if}
                {/each}
            </ol>
        </section>
    </div>
    <form onsubmit={(event) => {
        event.preventDefault()
        if (nyVara.trim() !== "") {
            varor = [...varor, { name: nyVara.trim(), köpt:false }];
            nyVara = "";
        }
    }}>
    <input type="text" bind:value={nyVara} placeholder="Add new item"/>
    <button type="submit">Add Item</button>
    </form>
</main>

<style>
.container{
    background-color: rgb(5, 42, 208);
    width: 60vw;
    height: 70vh;
    border-radius:  20px;
    display: grid;
    grid-template-rows: 1fr 9fr 1fr;
    margin: auto;
    display: grid;
    grid-template-rows: 1fr 8fr 1fr;
        
}
.container h1{
    text-align: center;
    border-radius: 20px;
    justify-content: center;
    align-items: center;
}
.categories_container{
    height: 100%;
    background-color: aqua;
    display: grid;
    grid-template-columns:repeat(2,1fr);
    grid-gap: 10px;
}
section{
height: 100%;
width:100%;
}


 .categories_container section:nth-child(odd){  /* vilket barn vill vi styla? */
    background-color: rgba(0, 0, 0, 0.1) /* svart bakgrund med 10% opacitet */
  }
 
  .categories_container section:nth-child(even){  /* vilket barn vill vi styla? */
    background-color: rgba(0, 0, 0, 0.3) /* svart bakgrund med 30% opacitet */
  }
  .categories_container h2{
    text-align: center;
    background-color: red;
    font-size: 2em;
  }
  li{
    border-bottom: 1px solid white;
  }

</style>