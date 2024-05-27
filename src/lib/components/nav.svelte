<script lang="ts">

</script>


<nav>
    <div class="inner">
        <a href="/" class="logo">
            <img src="../autonomint.svg" alt="Logo" width="140">
        </a>
        <div class="links">
            <a href="" class="link">
                Testnet Live · Join
                <img src="../arrow.svg" alt="" class="arrow" width="20">
            </a>
            <a href="" class="link">
                Docs
                <img src="../arrow.svg" alt="" class="arrow" width="20">
            </a>
            <a href="" class="link">
                Leaderboard
                <img src="../arrow.svg" alt="" class="arrow" width="20">                
            </a>
        </div>
        <div class="socials">
            <a href="https://x.com/autonomint" target="_blank" class="social">
                <img src="./x.svg" alt="X">
            </a>
            <a href="" target="_blank" class="social">
                <img src="./github.svg" alt="Github">
            </a>
            <a href="https://discord.com/invite/4QFaUTwjkU" target="_blank" class="social">
                <img src="./discord.svg" alt="Discord">
            </a>
            <a href="" class="button">Enter Dapp</a>
        </div>
    </div>
</nav>


<style>

    nav {
        width: 100%;
        height: 60px;
        position: absolute;
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

    @media screen and (max-width: 1000px) {
        .links {
            display: none;
        }
    }
</style>