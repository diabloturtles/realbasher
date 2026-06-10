<script>
    import { goto } from '$app/navigation';
    import { base } from '$app/paths';

    function handleSubmit(e) {
        e.preventDefault();
        const formData = new FormData(e.target);
        const search = formData.get('search');
        goto(base + '/search/' + search);
    }
</script>

<form onsubmit={handleSubmit}>
    <input type="text" name="search" placeholder="Sök upp en pokemon" />
</form>

<style>
    form {
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 10px;
    }

    input {
        padding: 12px 20px;
        font-size: 1.1rem;
        border: 2px solid #ccc;
        border-radius: 25px;
        width: 300px;
        outline: none;
        transition: border 0.2s;
    }

    input:focus {
        border-color: #4a90e2;
    }
</style>
