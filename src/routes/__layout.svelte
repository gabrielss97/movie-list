<script>
    import '../global.css'
    import Nav from '../components/Nav.svelte'

</script>

<svelte:head>
    <title>Movie Database | Svelte</title>
</svelte:head>

<Nav/>

<slot/>

<p>© 2022 Desenvolvido por Gabriel S. Salvador ❤️</p>

<style>
    p {
        margin: 2rem 0 ;
        text-align: center;
    }
</style>