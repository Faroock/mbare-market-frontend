<script>
    export let image
    export let banned = false
</script>

<picture class={banned ? 'banned' : ''}>
    <img src={image} alt='Imagen de carta'>
    <h1>BANNED</h1>
</picture>

<style>
    picture {
        position: fixed;
        top: 6em;
        right: 1em;
    }
    h1 {
        display: none;
        position: absolute;
    }
    .banned {
        position: absolute;
        display: inline-block;
        left: 10px;
        top: 130px;
        color: orange;
        font-size: 5em;
    }
</style>