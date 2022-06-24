<script>
    import blood from '../assets/Blood_drop.svg';
    export let costo;
</script>

<main>
    <picture>
        <img src={blood} height="20px" alt="blood cost">
        <span>{costo > 0 && costo < 10 ? costo : ''}</span>
    </picture>
</main>

<style>
    main {
        display: inline-block;
    }
    picture {
        position: relative;
        margin: 0;
        display: flex;
        align-items: flex-end;
    }
    span {
        position: absolute;
        color: white;
        left: calc(50% - 4px);
        font-size: 12px;
        /* bottom: 5px; */
    }
</style>