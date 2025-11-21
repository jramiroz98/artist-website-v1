<script>
	export let title = 'title';
</script>

<div class="heading">
	<h2>{title.toUpperCase()}</h2>
	<hr />
</div>

<style>
    .heading {
        width: fit-content;
        text-align: center;
        margin: 0 auto;
    }
    hr {
        width: 80%;
        margin: 0 auto;
        padding: 0;
        color: white;
    }
    h2 {
        color: white;
        margin: 0;
        padding: 0;
        font-family: 'Poppins', sans-serif;
        font-weight: 600;
        font-size: 2rem;
        /* font-size: 3.5rem; */
    }
    @media only screen and (min-width: 700px) {
        h2 {
            font-size: 3.5rem;
        }
    }
</style>