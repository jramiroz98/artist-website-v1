<script>
	import Modal from '$lib/components/Modal.svelte';

	let { image, title, spotify, apple, amazon, youtube } = $props();
	let showModal = $state(false);
</script>
<div>
	<img class="main-img p-6 md:p-4 md:w-[20rem] lg:w-[26rem]" onclick={() => (showModal = true)} src={image} alt="" />
	<div class="relative">
		<Modal bind:showModal>
			<!--{#snippet header()}-->
			<!--	<h2>-->
			<!--		modal-->
			<!--		<small><em>adjective</em> mod·al \ˈmō-dəl\</small>-->
			<!--	</h2>-->
			<!--{/snippet}-->
			<img class="modal-img" src={image} alt="" />
			<h2 class="font-semibold text-2xl my-2">{title.toUpperCase()}</h2>
			<div class="listening-platforms space-y-4 my-8">
				{#if spotify}
					<div>
						<a target="_blank" rel="noopener" href={spotify} class="streaming-button">
							<img class="icon-img" src="/images/icons/spotify-256.png" alt="spotify link" />
						</a>
					</div>
				{/if}
				{#if apple}
					<div>
						<a target="_blank" rel="noopener" href={apple} class="streaming-button">
							<img class="icon-img" src="/images/icons/apple-music.png" alt="apple music link" />
						</a>
					</div>
				{/if}
				{#if amazon}
					<div>
						<a target="_blank" rel="noopener" href={amazon} class="streaming-button">
							<img class="icon-img" src="/images/icons/amazon.png" alt="amazon music" />
						</a>
					</div>
				{/if}
				{#if youtube}
					<div>
						<a target="_blank" rel="noopener" href={youtube} class="streaming-button">
							<img class="icon-img" src="/images/icons/youtube.png" alt="youtube music" />
						</a>
					</div>
				{/if}
			</div>
		</Modal>
	</div>
</div>
<style>
    .main-img {
        transition: 0.2s;
        filter: drop-shadow(0px 1rem 1rem #484848);
        border-radius: 1.8rem;
    }
</style>
<!--<style>-->
<!--    .icon-img {-->
<!--        width: 100%;-->
<!--    }-->

<!--    .streaming-button {-->
<!--        word-wrap: normal;-->
<!--        width: 3rem;-->
<!--        padding: 1rem 3rem;-->
<!--        text-align: center;-->

<!--        background-color: black;-->
<!--        text-decoration: none;-->
<!--        color: white;-->
<!--        font-family: 'Poppins', sans-serif;-->
<!--        transition: 0.2s;-->
<!--        border-color: white;-->
<!--        border: solid;-->
<!--        border-width: 0.05rem;-->
<!--    }-->

<!--    .streaming-button:hover {-->
<!--        filter: invert(100%);-->
<!--    }-->

<!--    .listening-platforms {-->
<!--        display: grid;-->
<!--        grid-template-columns: repeat(2, minmax(0, 1fr));-->
<!--    }-->

<!--    h3,-->
<!--    h2 {-->
<!--        font-family: 'Poppins', sans-serif;-->
<!--        color: white;-->
<!--    }-->

<!--    h3 {-->
<!--        margin: auto;-->
<!--        text-align: center;-->
<!--    }-->

<!--    button {-->
<!--        margin: 0;-->
<!--        padding: 0;-->
<!--        border: none;-->
<!--        border-width: 0;-->
<!--    }-->

<!--.main-img {-->
<!--	&lt;!&ndash;margin: 2rem auto;&ndash;&gt;-->
<!--	&lt;!&ndash;padding: 0;&ndash;&gt;-->
<!--	&lt;!&ndash;border: none;&ndash;&gt;-->
<!--	&lt;!&ndash;width: 85vw;&ndash;&gt;-->
<!--	/* width: 19rem; */-->

<!--	transition: 0.2s;-->
<!--	filter: drop-shadow(0px 1rem 1rem #484848);-->
<!--}-->

<!--    .main-img:hover {-->
<!--        cursor: pointer;-->
<!--        transform: scale(1.05);-->
<!--        filter: drop-shadow(0px 0.5rem 1rem #222222);-->
<!--    }-->

<!--    .modal-img {-->
<!--        margin: 0;-->
<!--        padding: 0;-->
<!--        border: none;-->
<!--        width: 15rem;-->
<!--    }-->

<!--    @media only screen and (min-width: 700px) {-->
<!--        .main-img {-->
<!--            width: 14rem;-->
<!--        }-->

<!--        .modal-img {-->
<!--            width: 20rem;-->
<!--        }-->

<!--        .streaming-button {-->
<!--            width: 4rem;-->
<!--        }-->
<!--    }-->

<!--    @media only screen and (min-width: 1000px) {-->
<!--        .modal-img {-->
<!--            width: 20rem;-->
<!--        }-->

<!--        .main-img {-->
<!--            margin: 3rem;-->
<!--            width: 26rem;-->
<!--        }-->

<!--        .streaming-button {-->
<!--            padding: 1rem 3rem;-->
<!--        }-->
<!--    }-->
<!--</style>-->