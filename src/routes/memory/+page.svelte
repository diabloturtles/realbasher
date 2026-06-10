<script>





let imgs = ['https://picsum.photos/400/300?random=1',
'https://picsum.photos/400/300?random=2',
'https://picsum.photos/400/300?random=3',
'https://picsum.photos/400/300?random=4',
'https://picsum.photos/400/300?random=5',
'https://picsum.photos/400/300?random=6'];


let cards = $state([]);
for (let i = 0; i < imgs.length * 2; i++) {
    cards.push({
        image: imgs[i % imgs.length],
        flipped: false,
        matched: false
    });
}
let blueTurn = $state(true);
let bluePoints = $state(0);
let redPoints = $state(0);
let flipcount = $state(0);
let flippedcards = $state([]);

function flip(card) {
        if (card.flipped || card.matched) return;
        if (flipcount === 2) return;


        card.flipped = true;
        flipcount++;  
        flippedcards.push(card);

        if (flipcount === 2) {
            const  [card1, card2] = flippedcards;
            if (card1.image === card2.image) {
            if (blueTurn) {
                bluePoints++;
            } else {
                redPoints++;
            }
            card1.matched = true;
            card2.matched = true;
           } else {
                blueTurn = !blueTurn;
            }
        
            setTimeout(() => {
                cards.forEach((card) => {
                    if (!card.matched)
                        card.flipped = false;
                });
            }, 1000);
            flipcount = 0;
            flippedcards = [];
            cards = cards;
        }
}
</script>
<h1>Memory</h1>

<main>
 {#each cards as card}
    <div class="card" class:flipped={card.flipped} on:click={() => flip(card)}>

        <img class="front" src={card.image} alt="framsida"/>
        <img class="back" src="https://dragonslair.se/image/4180/Bicycle-Rider-Back-playing-cards-Green-2.png" alt="baksida"/>
    </div>
    {/each}
</main>
<aside class="blue"> 
    <p>Blue points: {bluePoints}</p>
</aside>
<aside>
    <p>Red points: {redPoints}</p>
</aside>
<aside class = "turn" class:blue= { blueTurn }>

</aside>
<style>
    

    h1{
        text-align: center;
    }

        
    main {
        display : grid;
        grid-template-columns: repeat(4, 100px);
        justify-content: center;
        align-items: center;
        gap: 10px;
    }
    .card {
        width: 100px;
        height: 100px;
        border: 1px solid black;

        display: flex;
        position: relative;
        justify-content:  center;
        align-items: center;
        backface-visibility: hidden;
        transform-style: preserve-3d;
        transition: transform 0.5s;

    }
    .card.flipped {
        transform: rotateY(180deg);
    }
    .card img {
    width:  100px;
    height: 100px;
    position: absolute;
    backface-visibility: hidden;
    }
    
    
  aside{
    width: 100px;
    height: 100px;
    position: fixed;
    bottom: 10px;
    right: 10px;
    background-color: red;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  p{
    font-size: 30px;
  }
  .blue {
    background-color: blue;
    left: 10px;
  }
  .turn {
    box-shadow: 0 0 10px 10px yellowgreen;
    z-index: -1;
  }
  .back {
    transform: rotateY(0deg);
  }      
  .front {
    transform: rotateY(180deg);
  }

</style>


