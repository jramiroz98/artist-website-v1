<script>
	import Heading from '$lib/components/Heading.svelte';
	import Song from '$lib/components/Song.svelte';
	import { fade } from 'svelte/transition';

	let visible = false;
	setTimeout(function() {
		visible = true;
	}, 500);
</script>

<div class="welcome">
	{#if visible}
		<img transition:fade class="logo" src="https://koalamcg.com/images/white-logo.png" alt="logo" />
	{/if}
	<div class="flex justify-center relative -bottom-60">
		<img class="scroll-icn bounce-1"
				 src="https://koalamcg.com/images/icons/scroll.png"
				 alt="scroll down" />
	</div>
</div>
<div class="music bg-black py-20">
	<Heading title="music" />
	<div class="songs md:flex md:flex-wrap my-12 justify-center relative">
		<Song
			image="https://is1-ssl.mzstatic.com/image/thumb/Music126/v4/5c/19/43/5c194395-528a-3e82-b194-a4712542f1b7/artwork.jpg/632x632bb.webp"
			title="Hotsteppa"
			spotify="https://open.spotify.com/album/6FgUvBOEuXMW77kSjrJeit"
			amazon="https://www.amazon.es/Hotsteppa-Radio-Edit/dp/B0CTGKVXXH"
			youtube="https://www.youtube.com/watch?v=0tVeSPqLsFE"
			apple="https://music.apple.com/gb/album/hotsteppa-radio-edit-single/1728621384"
		/>
		<Song
			image="https://is1-ssl.mzstatic.com/image/thumb/Music126/v4/5c/19/43/5c194395-528a-3e82-b194-a4712542f1b7/artwork.jpg/632x632bb.webp"
			title="Hotsteppa"
			spotify="https://open.spotify.com/album/6FgUvBOEuXMW77kSjrJeit"
			amazon="https://www.amazon.es/Hotsteppa-Radio-Edit/dp/B0CTGKVXXH"
			youtube="https://www.youtube.com/watch?v=0tVeSPqLsFE"
			apple="https://music.apple.com/gb/album/hotsteppa-radio-edit-single/1728621384"
		/>
		<Song
			image="https://is1-ssl.mzstatic.com/image/thumb/Music126/v4/5c/19/43/5c194395-528a-3e82-b194-a4712542f1b7/artwork.jpg/632x632bb.webp"
			title="Hotsteppa"
			spotify="https://open.spotify.com/album/6FgUvBOEuXMW77kSjrJeit"
			amazon="https://www.amazon.es/Hotsteppa-Radio-Edit/dp/B0CTGKVXXH"
			youtube="https://www.youtube.com/watch?v=0tVeSPqLsFE"
			apple="https://music.apple.com/gb/album/hotsteppa-radio-edit-single/1728621384"
		/>
		<Song
			image="https://is1-ssl.mzstatic.com/image/thumb/Music126/v4/5c/19/43/5c194395-528a-3e82-b194-a4712542f1b7/artwork.jpg/632x632bb.webp"
			title="Hotsteppa"
			spotify="https://open.spotify.com/album/6FgUvBOEuXMW77kSjrJeit"
			amazon="https://www.amazon.es/Hotsteppa-Radio-Edit/dp/B0CTGKVXXH"
			youtube="https://www.youtube.com/watch?v=0tVeSPqLsFE"
			apple="https://music.apple.com/gb/album/hotsteppa-radio-edit-single/1728621384"
		/>
		<Song
			image="https://is1-ssl.mzstatic.com/image/thumb/Music126/v4/5c/19/43/5c194395-528a-3e82-b194-a4712542f1b7/artwork.jpg/632x632bb.webp"
			title="Hotsteppa"
			spotify="https://open.spotify.com/album/6FgUvBOEuXMW77kSjrJeit"
			amazon="https://www.amazon.es/Hotsteppa-Radio-Edit/dp/B0CTGKVXXH"
			youtube="https://www.youtube.com/watch?v=0tVeSPqLsFE"
			apple="https://music.apple.com/gb/album/hotsteppa-radio-edit-single/1728621384"
		/>
		<Song
			image="https://is1-ssl.mzstatic.com/image/thumb/Music126/v4/5c/19/43/5c194395-528a-3e82-b194-a4712542f1b7/artwork.jpg/632x632bb.webp"
			title="Hotsteppa"
			spotify="https://open.spotify.com/album/6FgUvBOEuXMW77kSjrJeit"
			amazon="https://www.amazon.es/Hotsteppa-Radio-Edit/dp/B0CTGKVXXH"
			youtube="https://www.youtube.com/watch?v=0tVeSPqLsFE"
			apple="https://music.apple.com/gb/album/hotsteppa-radio-edit-single/1728621384"
		/>

	</div>
</div>

<div class="youtube bg-blue-950 py-20 ">
	<Heading title="Youtube" />
	<div class="flex flex-col space-y-6 justify-center items-center py-8">
		<iframe
			class="w-[22rem] h-[15rem]"
			src="https://www.youtube.com/embed/d-dvuFZeNAQ?si=wZhEA_qT8puJrIvq&amp;controls=0"
			title="YouTube video player"
			frameborder="0"
			allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
			allowfullscreen
		/>
	</div>
</div>


<div class="bg-black py-8">
	<Heading title="Biografia" />
	<div class="text-white px-2 text-center">
		<!-- <img src="/images/songs/smyl.png" style="width: 30%;" alt="" /> -->
		<p>
			Koala McGiver es un Dj y Productor Hondureño. Con más de 7 años de experiencia en producción
			musical, presenta música de alta calidad y un gusto muy variado. Los Dj Sets son movidos y
			para un publico alegre y cálido. Sus producciones han sido reproducidas por DJs alrededor del
			mundo, así como unreleased mashups y remixes.
		</p>
		<br />
		<p>
			Cabe mencionar que dentro de otros talentos se destacan sus animaciones y renderizados en 3D,
			las cuales se utilizan en algunas de sus presentaciones.
		</p>
	</div>
</div>

<div class="contact bg-black">
	<Heading title="Bookings" />
	<a style="text-decoration: none; color: white;" href="mailto:koalamcgiver98@gmail.com">
		<p class="email">koalamcgiver98@gmail.com</p>
	</a>
	<div class="social-media">
		<a target="_blank" rel="noopener" href="https://www.instagram.com/koalamcg_98/?hl=en">
			<img class="social-icn" src="/images/icons/instagram.png" alt="instagram" />
		</a>
		<a target="_blank" rel="noopener" href="https://www.youtube.com/@koalamcgiver/featured">
			<img class="social-icn" src="/images/icons/youtube.png" alt="youtube" />
		</a>
		<a
			target="_blank"
			rel="noopener"
			href="https://open.spotify.com/artist/73nBtoghfH7KJK53JgiAwl?si=lagp8aSqQkOEGjDJH_1Lyw"
		>
			<img class="social-icn" src="/images/icons/spotify-256.png" alt="spotify" />
		</a>
		<a
			target="_blank"
			rel="noopener"
			href="https://music.apple.com/us/artist/koala-mcgiver/1534748006"
		>
			<img class="social-icn" src="/images/icons/apple-music.png" alt="apple music" />
		</a>
	</div>
</div>

<style>
    .logo {
        width: 15rem;
        display: flex;
        /* justify-content: center; */
        text-align: center;
        margin: auto;
        padding-top: 35vh;
    }

    /*iframe {*/
    /*    width: 15rem;*/
    /*    height: auto;*/
    /*}*/

    .bounce-1 {
        animation-name: bounce-1;
        animation-timing-function: ease;
    }

    @keyframes bounce-1 {
        0% {
            transform: translateY(0);
        }
        50% {
            transform: scale(1.05) translateY(-20px);
        }

        100% {
            transform: translateY(0);
        }
    }

    .scroll-icn {
        animation-duration: 1.5s;
        animation-iteration-count: infinite;
        width: 2rem;
        /*position: absolute;*/
        /*bottom: 3rem;*/
        /*left: 46%;*/
    }

    .youtube {
        background-image: url('/images/logo-bg.jpg');
        min-height: 100vh;
        background-attachment: fixed;
        background-position: center;
        background-repeat: no-repeat;
        background-size: cover;
    }

    .set-img {
        width: 15rem;
        /* width: 30rem; */
        /* padding: 10rem 5rem; */
        padding: 1rem 0rem;
        margin: auto;
    }

    .sets {
        /* display: flex; */
        display: block;
        justify-content: center;
        text-align: center;
        margin-bottom: 6rem;
    }

    .welcome {
        background: url('https://images.unsplash.com/photo-1763688506750-0da09fe27324?q=80&w=2832&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D');
        min-height: 100vh;
        background-attachment: fixed;
        background-attachment: scroll;
        background-position: center;
        background-repeat: no-repeat;
        background-size: cover;
        -webkit-background-size: cover;
        -moz-background-size: cover;
        -o-background-size: cover;
    }

    .social-icn {
        width: 3rem;
        height: 100%;
        margin: 2rem 1rem;
        transition: 0.2s;
    }

    .social-icn:hover {
        transform: scale(1.1);
    }

    .social-media {
        display: flex;
        /* display: flex; */
        justify-content: center;
        align-items: center;
        padding-bottom: 10rem;
    }

    .email {
        margin: 1rem;
        font-size: 0.8rem;
    }

    .contact {
        color: white;
        font-family: 'Poppins', sans-serif;
        margin: auto;
        text-align: center;
    }

    .bio {
        font-family: 'Poppins', sans-serif;
        background-color: rgb(27, 27, 27);
        text-align: center;
        margin-top: 1rem;
        margin-bottom: 6rem;

        padding: 1rem 2rem;
        /* padding: 8rem 2rem; */
        display: block;
        color: white;
    }

    .embedded {
        margin: 1rem auto;
        text-align: center;
        padding: 1rem 0;
        /* padding: 5rem 0; */
    }

    /*.songs {*/
    /*    !* display: flex; *!*/
    /*    text-align: center;*/
    /*    justify-content: center;*/
    /*    margin: 4rem auto;*/
    /*}*/

    @media only screen and (min-width: 700px) {
        .logo {
            width: 24rem;
        }

        /*iframe {*/
        /*    width: 22rem;*/
        /*    height: 100%;*/
        /*}*/
        .youtube {
            min-height: 50vh;
        }

        .set-img {
            /* display: flex; */
            width: 20rem;
            padding: 5rem 1rem;
        }

        .email {
            font-size: 1.5rem;
            margin: 3rem;
        }

        .social-icn {
            width: 4rem;
            margin: 2rem 3rem;
        }
    }

    @media only screen and (min-width: 1000px) {
        /*.songs {*/
        /*    display: flex;*/
        /*    flex-wrap: wrap;*/
        /*    margin: 4rem 10rem;*/
        /*}*/
        /*iframe {*/
        /*    width: 30rem;*/
        /*    height: 15rem;*/
        /*}*/
        .set-img {
            width: 30rem;
        }

        .bio {
            padding: 8rem 20rem;
        }

        .email {
            margin: 5rem;
            font-size: 2rem;
        }

        .social-icn {
            width: 5rem;
        }
    }
</style>