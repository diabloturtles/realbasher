
<!--Delar upp sidan i två delar-->
<main>
  <div>

    <h1  class="name">Ossian  </h1>
    <h2>Här har jppgifter jag gjort i samband med webbutveckling i årskurs 2 på Maja Beskowgymnasiet!</h2>
    <h3>vecklingsresa:</h3>
    <!--Under denna kommer vi lägga till fler element-->
    <p id="inspo">h
    "The only way to learn a new programming language is by writing programs in it." - <strong>Dennis Ritchie</strong>, creator of the C programming language.
</p>

<p style="background-color:pink">
    "Every great developer you know got there by solving problems they were unqualified to solve until they actually did it." - <span>Patrick McKenzie, software engineer and entrepreneur</span>.
</p>


  </div>
    <!--Här kommer vi lägga till en bild senare i uppgiften 1.2.4 Extra styling-->  

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1440 320"><path fill="#0099ff" fill-opacity="1" d="M0,288L51.4,192L102.9,256L154.3,128L205.7,32L257.1,96L308.6,0L360,256L411.4,224L462.9,32L514.3,0L565.7,32L617.1,224L668.6,32L720,288L771.4,128L822.9,96L874.3,32L925.7,224L977.1,128L1028.6,128L1080,192L1131.4,288L1182.9,32L1234.3,0L1285.7,0L1337.1,192L1388.6,64L1440,128L1440,320L1388.6,320L1337.1,320L1285.7,320L1234.3,320L1182.9,320L1131.4,320L1080,320L1028.6,320L977.1,320L925.7,320L874.3,320L822.9,320L771.4,320L720,320L668.6,320L617.1,320L565.7,320L514.3,320L462.9,320L411.4,320L360,320L308.6,320L257.1,320L205.7,320L154.3,320L102.9,320L51.4,320L0,320Z"></path></svg>


</main>

<style>
  main{
    /*Styling för att dela upp sidan i två delar. */
    /*Vi kommer gå igenom detta i detalj senare*/
    margin: auto;
    width: 80vw;
    height: 70vh;
    display: grid;
    grid-template-columns: repeat(2,50%);
    overflow: hidden;
  } 
  div{
    /*Styling för att centrera texten i behållaren*/
    margin: auto;
  }

    
  

  /* Vi skiljer elementen med ett kommatecken(,) för att ge möjligheten till att ge flera element samma styling*/
h1, h2, h3, p {
  display: inline;
  /*Ger utrymme mellan element*/
  margin: 10px;
}
        


#inspo{
    font-family: courier;
    font-size: 160%;
}

span{
    color: green;
}

                

                
.name{
    font-family:'Gill Sans';
    font-size: 50px;
}
    




  </style>
