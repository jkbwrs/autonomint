<section id="waitlist">
    <div class="inner">
        <div class="forms">
            <form action="" class="container">
                <h3>Join Waitlist</h3>
                <p class="subheadline">Be among the first ones to experience our Dapp. </p>
                <div class="wrapper">
                    <input type="email" class="email" placeholder="Enter E-mail ID">
                    <button class="button" style="width: 100%">Join Waitlist</button>
                </div>
            </form>
            <slot></slot>
        </div>
    </div>
</section>


<style>

    section {
        z-index: 10;
        padding: 100px 0;
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

    .forms {
        width: 100%;
        display: grid;
        grid-template-columns: 1fr 1fr;
        justify-content: center;
        align-items: center;
        gap: 32px;
        margin-top: 60px;
    }

    .container {
        height: 400px;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        padding: 40px;
        background-color: #fff;
        border: 1px solid var(--darkgrey);
        border-radius: 20px;
    }

    .email {
        height: 48px;
        width: 300px;
        padding: 6px 12px;
        border: 1px solid var(--darkgrey);
        border-radius: 8px;
    }

    .email:focus {
        outline: none;
        border: 1px solid var(--black);
    }

    .wrapper {
        display: flex;
        justify-content: space-between;
        align-items: center;
        flex-direction: column;
        gap: 12px;
        width: 100%;
        max-width: 300px;
        margin-top: 12px;
        margin-bottom: 12px;
    }

</style>