<script>
import { create_animation } from "svelte/internal";
import BloodCost from "./BloodCost.svelte";

    import ImageCard from "./ImageCard.svelte"

    let image = ''
    let showImagen = false
    let libreria = []
    fetch('https://mbare-market-backend-production.up.railway.app/all_cards?type=Library&page_size=30')
    .then(response => response.json())
    .then(data => libreria = data.data)
    const showImage = event => {
        image = event.target.getAttribute('data')
        showImagen = true
    }
</script>
<main>
    {#if libreria.length > 0}
        <ul>
            {#each libreria as carta} 
                <!-- svelte-ignore a11y-mouse-events-have-key-events -->
                <li id={carta.id}
                    class={carta.banned ? 'banned' : ''}
                    on:mouseover={showImage}
                >
                    <span data={carta.url}>{carta._name}</span>
                    <span data={carta.url}>{carta.types.join('/')}</span>
                    {#if carta.blood_cost}
                        <BloodCost costo={carta.blood_cost} />
                    {:else}
                        {#if carta.pool_cost}
                            <span data={carta.url}>{carta.pool_cost} pool</span>
                        {:else}
                            <span data={carta.url}></span>
                        {/if}
                    {/if}
                    <span data={carta.url}>{carta.clans.join('/')}</span>
                    <span data={carta.url}>{carta.disciplines.join(' ')}</span>
                    <span data={carta.url}>{carta.combo || ''}</span>
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
    li {
        display: grid;
        grid-template-columns: 5fr 4fr 1fr 4fr 3fr 1fr;
        justify-items: start;
    }
    span {
        cursor: default;
    }
    .banned {
        text-decoration: line-through;
    }
</style>