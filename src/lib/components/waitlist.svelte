<script>
    import Pin from "./pin.svelte";


</script>


<section id="waitlist">
    <div class="inner">
        <h3>Join Waitlist</h3>
        <p>Be among the first ones to experience our Dapp. </p>
        <div class="forms">
            <form action="">
                <input type="email" class="email" placeholder="Enter E-mail ID">
                <button class="button">Join Waitlist</button>
            </form>
            <Pin />
        </div>
    </div>
</section>


<style>

    section {
        z-index: 10;
        padding: 100px 0;
        background-color: var(--green);
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .inner {
        width: 90%;
        max-width: 1200px;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
    }

    .forms {
        display: flex;
        justify-content: center;
        align-items: center;
        gap: 32px;
        margin-top: 60px;
    }

    .email {
        height: 48px;
        width: 300px;
    }

</style>