<script lang="ts">
    import { onMount } from "svelte";

    let nav: HTMLElement;
    let scrollY = 0;

    function handleScroll() {
        const maxScroll = 200;
        const progress = Math.min(scrollY / maxScroll, 1);

        const blurValue = progress * 12;
        const saturateValue = 100 + progress * 60;
        const backgroundColorValue = `rgba(228, 232, 230, ${0.8 * progress})`;

        nav.style.backdropFilter = `blur(${blurValue}px) saturate(${saturateValue}%)`;
        nav.style.backgroundColor = backgroundColorValue;
    }

    onMount(() => {
        window.addEventListener("scroll", handleScroll);

        return () => {
            window.removeEventListener("scroll", handleScroll);
        };
    });
</script>

<svelte:window bind:scrollY on:scroll={handleScroll} />

<nav bind:this={nav}>
    <div class="inner">
        <a href="/" class="logo">
            <img src="../autonomint.svg" alt="Logo" width="140" />
        </a>
        <div class="links">
            <a href="#" class="link">
                Testnet Live · Join
                <img src="../arrow.svg" alt="" class="arrow" width="20" />
            </a>
            <a href="#" class="link">
                Docs
                <img src="../arrow.svg" alt="" class="arrow" width="20" />
            </a>
            <a href="#" class="link">
                Leaderboard
                <img src="../arrow.svg" alt="" class="arrow" width="20" />
            </a>
        </div>
        <div class="socials">
            <a href="https://x.com/autonomint" target="_blank" class="social">
                <img src="./x.svg" alt="X" height="100%" />
            </a>
            <a href="#" target="_blank" class="social">
                <img src="./github.svg" alt="Github" height="100%" />
            </a>
            <a
                href="https://discord.com/invite/4QFaUTwjkU"
                target="_blank"
                class="social"
            >
                <img src="./discord.svg" alt="Discord" height="100%" />
            </a>
            <a href="#" class="button">Enter Dapp</a>
        </div>
    </div>
</nav>

<style>
    nav {
        width: 100%;
        height: 60px;
        position: fixed;
        inset: 0 0 auto 0;
        z-index: 100;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .inner {
        width: 90%;
        max-width: 1200px;
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    .links {
        display: flex;
        justify-content: center;
        align-items: center;
        gap: 32px;
    }

    .link {
        border-bottom: 1px solid var(--darkgrey);
        text-decoration: none;
        color: var(--black);
        padding-bottom: 4px;
        display: flex;
        justify-content: center;
        align-items: center;
        gap: 6px;
    }

    .arrow {
        transition: all 400ms ease;
    }

    .link:hover .arrow {
        bottom: 4px;
        left: 4px;
    }

    .socials {
        display: flex;
        justify-content: center;
        align-items: center;
        gap: 20px;
    }

    .social {
        width: 20px;
        height: 16px;
    }

    @media screen and (max-width: 1000px) {
        .links {
            display: none;
        }

        .social {
            width: 16px;
            height: 14px;
        }
    }

    @media screen and (max-width: 500px) {
        .social {
            display: none;
        }
    }
</style>
