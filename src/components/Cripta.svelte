<script>
    import ImageCard from "./ImageCard.svelte"

    let image = ''
    let showImagen = false
    let cripta = []
    fetch('https://mbare-market-backend-production.up.railway.app/all_cards?type=Vampire&page_size=30')
    .then(response => response.json())
    .then(data => cripta = data.data)
    const showImage = event => {
        image = event.target.getAttribute('data')
        showImagen = true
    }
</script>
<main>
    {#if cripta.length > 0}
        <ul>
            {#each cripta as vampire}
                <!-- svelte-ignore a11y-mouse-events-have-key-events -->
                <li id={vampire.id}
                    class={vampire.banned ? 'banned' : ''}
                    on:mouseover={showImage}
                >
                    <span data={vampire.url}>{vampire.group}</span>
                    <span data={vampire.url}>{vampire._name}</span>
                    <span data={vampire.url}>{vampire.clans[0]}</span>
                    <span data={vampire.url}>{vampire.capacity}</span>
                    <span data={vampire.url}>{vampire.disciplines.join(' ')}</span>
                    <span data={vampire.url}>{vampire.title || ''}</span>
                </li>
            {/each}
        </ul>
        {#if showImagen && image}
            <ImageCard image={image} />
        {/if}
    {:else}
        <p>Por favor espere mientras se cargan los datos</p>
    {/if}
</main>
<style>
    ul {
        padding: 0;
    }
    li {
        display: grid;
        grid-template-columns: 1fr 5fr 4fr 1fr 4fr 3fr;
        justify-items: start;
        align-content: flex-start;
    }
    li:nth-child(odd) {
        background-color: #ffd700;
    }
    li:nth-child(even) {
        background-color: #c7be8e;
    }
    span {
        display: inline-block;
        cursor: default;
    }
    .banned {
        text-decoration: line-through;
    }
    @media (max-width: 768px) {
        li {
            grid-template-columns: 4fr 3fr 1fr;
        }
        span:first-child, span:nth-last-child(-n+2) {
            display: none;
        }
    }
</style>