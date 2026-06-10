<script>
    import ElizaBot from 'elizabot';
    import { enhance } from '$app/forms';

    const eliza = new ElizaBot();
    function now() {
        return new Date().toLocaleTimeString('sv-SE', { hour: '2-digit', minute: '2-digit' });
    }

    let chat = $state([{ user: 'Eliza', message: eliza.getInitial(), time: now() }]);

    async function write(message) {
        chat.push({ user: 'User', message: message, time: now() });

        var element = document.getElementById("visible");
        element.style.display = "flex";

        // random delay for Eliza's response time
        await new Promise((r) => setTimeout(r, 1000 + Math.random() * 1000));

        element.style.display = "none";

        chat.push({ user: 'Eliza', message: eliza.transform(message), time: now() });
    }
</script>

<main>
    <section>
        {#each chat as msg}
            <article class={msg.user} data-user={msg.user} data-time={msg.time}>
                <p>{msg.message}</p>
            </article>
        {/each}
        <article id="visible">
            <span class="circle"></span>
            <span class="circle"></span>
            <span class="circle"></span>
        </article>
    </section>

    <form method="post" use:enhance={({ formElement, formData, cancel }) => {
        cancel();
        const text = formData.get("text");
        write(text);
        formElement.reset();
    }}>
        <input type="text" name="text" placeholder="Skriv ett meddelande..." />
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

    #visible {
        width: 100px;
        height: 60px;
        padding: 0;
        display: none;
        align-items: center;
        justify-content: space-evenly;
    }

    @keyframes typing {
        0%   { transform: scale(1); }
        25%  { transform: scale(1); }
        50%  { transform: scale(1.4); }
        100% { transform: scale(1); }
    }

    .circle {
        width: 10px;
        height: 10px;
        border-radius: 50%;
        background-color: #888;
        animation: typing 1000ms ease-in-out infinite;
    }

    .circle:nth-child(1) { animation-delay: 0ms; }
    .circle:nth-child(2) { animation-delay: 333ms; }
    .circle:nth-child(3) { animation-delay: 666ms; }

    article::before {
        content: attr(data-user);
        font-weight: bold;
        font-size: 0.85em;
        display: block;
    }

    article::after {
        content: attr(data-time);
        font-size: 0.8em;
        color: gray;
        display: block;
    }

    input::placeholder {
        color: #aaa;
        font-style: italic;
    }

    .Eliza {
        background-color: #d1e7dd;
        text-align: left;
        margin-right: auto;
    }

    .User {
        background-color: #cfe2ff;
        text-align: right;
        margin-left: auto;
    }

    article:hover {
        filter: brightness(1.1);
    }

    input:focus {
        outline: 2px solid #4a90e2;
        background-color: #eef4ff;
    }

    article:first-child {
        background-color: #a8d5b5;
    }

    article, input {
        margin: 10px;
        padding: 10px;
        border-radius: 10px;
        background-color: #ffffff;
        width: 90%;
    }
</style>
