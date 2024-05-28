<script lang="ts">
    import { onMount } from "svelte";
    import { scroll } from "motion";
    import Nav from "$lib/components/nav.svelte";
    import Footer from "$lib/components/footer.svelte";
    import Waitlist from "$lib/components/waitlist.svelte";
    import Pin from "$lib/components/pin.svelte";

    let video: HTMLVideoElement;
    let pin: string = ""

    onMount(() => {
        const handleScroll = ({ y }: { y: { progress: number } }) => {
            if (video && video.readyState > 0) {
                const currentTime = video.duration * y.progress;
                if (Math.abs(video.currentTime - currentTime) > 0.1) {
                    video.currentTime = currentTime;
                }
            }
        };

        scroll(handleScroll, {
            target: document.documentElement,
            offset: ["start start", "end end"]
        });
    });

    $: console.log(pin)
</script>

<svelte:head>
    <title>Autonomint</title>
    <meta name="description" content="The world’s first fully decentralized stablecoin protocol backed by decentralized derivatives.">
</svelte:head>

<Nav />

<aside>
    <video controls={false} preload="auto" muted autoplay playsinline bind:this={video}>
        <source src="./bg.mp4" type="video/mp4">
        <!-- <source src="./bg.webm" type="video/webm"> -->
        Your browser does not support the video tag.
    </video>
</aside>

<header>
    <p>The world’s first fully decentralized stablecoin protocol backed by decentralized derivatives.</p>
    <h1>Unlock the <span>Hidden</span> CAPITAL</h1>
    <div class="buttons">
        <a href="/#waitlist" class="button">Join Waitlist</a>
        <a href="/#waitlist" class="button">Enter Invitecode</a>
    </div>
</header>

<main>
    <h2>Get 100% synthetic LTV from a <br> <span>stablecoin</span> lending protocol</h2>
    <h2><span>Earn yield</span> on our <br> ‘Colored’ stablecoin USDa</h2>
    <h2>Get upto 5X leverage while <br> <span>earning derivative</span> fees</h2>
</main>

<Waitlist>
    <Pin bind:code={pin} />
</Waitlist>

<Footer />

<style>
    header {
        height: 100vh;
        width: 100%;
        display: flex;
        justify-content: flex-start;
        align-items: center;
        flex-direction: column;
        text-align: center;
        padding-top: 20vh;
    }

    aside {
        position: fixed;
        height: 100vh;
        width: 100%;
        z-index: 0;
        pointer-events: none;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    video {
        width: 100%;
        height: 100%;
        object-fit: cover;
        object-position: center top;
    }

    main {
        height: 200vh;
        display: flex;
        flex-direction: column;
        justify-content: space-around;
        align-items: center;
        text-align: center;
    }

    .buttons {
        display: flex;
        justify-content: center;
        align-items: center;
        gap: 12px;
        margin-top: 20px;
    }

</style>
