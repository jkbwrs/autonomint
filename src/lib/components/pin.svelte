<script lang="ts">
    let pins: string[] = ["", "", "", "", ""];
    let inputs: HTMLInputElement[] = [];

    const handleInput = (index: number, event: Event) => {
        const input = event.target as HTMLInputElement;
        const value = input.value.trim();

        if (/^\d$/.test(value)) {
            pins[index] = value;
            if (index < inputs.length - 1) {
                inputs[index + 1].focus();
            }
        } else {
            input.value = "";
        }
    };

    const handleKeyDown = (index: number, event: KeyboardEvent) => {
        if (event.key === "Backspace" && !pins[index] && index > 0) {
            inputs[index - 1].focus();
        }
    };
</script>

<div class="container">
    {#each pins as pin, index}
        <input
            class="pin"
            type="number"
            maxlength="1"
            placeholder="_"
            bind:this={inputs[index]}
            bind:value={pins[index]}
            on:input={(e) => handleInput(index, e)}
            on:keydown={(e) => handleKeyDown(index, e)}
        />
    {/each}
    <div class="redeem-button">Redeem Invite Code ➔</div>
</div>

<style>
    .container {
        display: flex;
        gap: 10px;
        justify-content: center;
        align-items: center;
        padding: 40px;
        background-color: #fff;
        border: 1px solid var(--darkgrey);
        border-radius: 20px;
    }

    input {
        width: 48px;
        height: 48px;
        text-align: center;
        font-size: 24px;
        border: 1px solid var(--green);
    }

    input:focus {
        border: 1px solid var(--black);
        outline: none;
    }

    .redeem-button {
        height: 40px;
        display: flex;
        align-items: center;
        padding: 0 10px;
        border: 1px solid black;
        cursor: pointer;
    }

</style>
