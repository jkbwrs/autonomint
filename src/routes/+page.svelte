<script lang="ts">
    import { onMount } from "svelte";
    import { scroll } from "motion";
    import Nav from "$lib/components/nav.svelte";
    import Footer from "$lib/components/footer.svelte";
    import Waitlist from "$lib/components/waitlist.svelte";
    import Pin from "$lib/components/pin.svelte";
    import { tweened } from "svelte/motion"

    let video: HTMLVideoElement;
    let pin: string = ""
    const currentTime = tweened(0, {
        duration: 10,
    })

    onMount(() => {
        video.pause()
        currentTime.subscribe(value => {
            if (video && video.readyState >= 2) {
                video.currentTime = value
            }
        })

        const handleScroll = ({ y }: { y: { progress: number } }) => {
            if (video && video.readyState >= 2) {
                const newTime = video.duration * y.progress
                currentTime.set(newTime)
            }
        }

        const unscroll = scroll(handleScroll, {
            target: document.documentElement,
            offset: ["start start", "end end"]
        })

        return () => {
            unscroll()
        }
    })

</script>

<svelte:head>
    <title>Autonomint</title>
    <meta name="description" content="The world’s first fully decentralized stablecoin protocol backed by decentralized derivatives.">
</svelte:head>

<Nav />

<aside>
    <video controls={false} preload="auto" muted autoplay={false} playsinline loop={false} bind:this={video}>
        <source src="../bg.mp4" type="video/mp4">
        <!-- <source src="./bg.webm" type="video/webm"> -->
        Your browser does not support the video tag.
    </video>
</aside>

<header>
    <div class="buttons">
        <div class="block">
            <div class="text-block" style="font-size: 8px; color: var(--lightgrey)">Secured spot in the</div>
            <img src="../acc.svg" width="100" alt="Mode Yield Accelerator Logo" class="acce-logo">
        </div>
        <div class="block">
            <div class="text-block" style="font-size: 8px; color: var(--lightgrey)">Winners of</div>
            <img src="../soonami.webp" width="80" alt="Soonami Logo" style="margin-top: -4px">
            <div class="text-block" style="font-size: 8px; color: var(--lightgrey)">Venturethon</div>
        </div>
    </div>
    <p style="max-width: 90%">The world’s first fully decentralized stablecoin protocol backed by decentralized derivatives.</p>
    <h1>Unlock the <span>Hidden</span> CAPITAL</h1>
    <div class="buttons">
        <a href="/#waitlist" class="button">Join Waitlist</a>
        <a href="/#waitlist" class="button">Enter Invite Code</a>
    </div>
</header>

<main>
    <h2>Get 100% synthetic LTV from a <span>stablecoin</span> lending protocol</h2>
    <h2><span>Earn yield</span> on our ‘Colored’ stablecoin USDa</h2>
    <h2>Get upto 5X leverage while <span>earning derivative</span> fees</h2>
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

    .block {
        height: 42px;
        grid-column-gap: 8px;
        grid-row-gap: 8px;
        -webkit-backdrop-filter: blur(4px);
        backdrop-filter: blur(4px);
        background-color: var(--black);
        color: #fff;
        border-radius: 40px;
        margin-bottom: 10px;
        padding: 10px 16px;
        display: flex;
        justify-content: center;
        align-items: center;
        position: relative;
        text-transform: uppercase;
    }

    .acce-logo {
        width: 50px;
    }

    .block::before {
         content: '';
         position: absolute;
         top: -1px;
         left: -1px;
         right: -1px;
         bottom: -1px;
         border-radius: inherit;
         box-shadow: 0 0 10px var(--green);
         animation: glowing 6s linear infinite;
      }

      @keyframes glowing {
         0% {
            box-shadow: 0 -2px 2px var(--green);
         }
         25% {
            box-shadow: 2px 0 2px var(--green);
         }
         50% {
            box-shadow: 0 2px 2px var(--green);
         }
         75% {
            box-shadow: -2px 0 2px var(--green);
         }
         100% {
            box-shadow: 0 -2px 2px var(--green);
         }
      }

      @media screen and (max-width: 400px) {
        .buttons {
            flex-direction: column;
        }
      }
   

</style>
