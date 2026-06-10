<script>
    import ElizaBot from 'elizabot';

    const eliza = new ElizaBot();
    let chat = $state([{ user: 'Eliza', message: eliza.getInitial() }]);
</script>

<main>
    <section>
        {#each chat as msg}
            <article>
                <p>{msg.message}</p>
            </article>
        {/each}
    </section>

    <form>
        <input type="text" placeholder="Skriv ett meddelande..." />
    </form>
</main>












<style>
    main {
        width: 60vw;
        height: 70vh;
        margin: auto;
        padding: 10px;
        background-color: #f0f4f8;
        display: grid;
        grid-template-rows: 90% 10%;
    }

    section {
        overflow-y: scroll;
    }

    form {
        display: flex;
        align-items: center;
    }

    article, input {
        margin: 10px;
        padding: 10px;
        border-radius: 10px;
        background-color: #ffffff;
        width: 90%;
    }
</style>
