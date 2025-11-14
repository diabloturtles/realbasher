<script>
let image = "https://picsum.photos/id/70/367/267"
let photo = "https://picsum.photos/id/88/367/267"
let picture = "https://picsum.photos/id/93/367/267"

</script>



<main>
        <h1> Photoapp</h1>
        <p> elias är fruzzy </p>

</main>


<div class=photos>
    <div class='image-wrapper'>
        <img src={image} alt="Flexbox egenskaper"></div>
        
    <div class='image-wrapper'>
        <img src={photo} alt="Flexbox egenskaper"></div>
     <div class='image-wrapper'>
        <img src={picture} alt="Flexbox egenskaper"></div>
    </div>
<style>
    
h1{
    text-align: center;
    font-size: 50px;
    margin: 20px;
    color: grey;
}
    .photos{
        display:flex;
        max-width: 100vw;
        height: 40vh;   
        align-items:center; 
        justify-content: center;
        flex-wrap: wrap;
    }

    .image-wrapper{
        width: 100%;
        flex: 1;
        margin:10px;
        height: 100%;
    }

    .image-wrapper img{
        width: 100%;
        height: 100%;
        border: 2px solid white;
        box-shadow: 4px 8px 0px rgba(0,0,0,0.2);
        border-radius: 20px;
        background-color: rgb(12, 11, 11);
    }
    .image-wrapper:hover { flex-grow:2; }
    .image-wrapper:active { transform: scale(0.9); }
</style>