<script lang="ts">
    export let code: string = ""

    let pins: string[] = ["", "", "", "", ""]
    let inputs: HTMLInputElement[] = []

    const handleInput = (index: number, event: Event) => {
        const input = event.target as HTMLInputElement
        const value = input.value.trim()

        if (/^\d$/.test(value)) {
            pins[index] = value
            if (index < inputs.length - 1) {
                inputs[index + 1].focus()
            }
        } else {
            input.value = ""
        }
    }

    const handleKeyDown = (index: number, event: KeyboardEvent) => {
        if (event.key === "Backspace" && !pins[index] && index > 0) {
            inputs[index - 1].focus()
        }
    }

    $: code = pins.join("")
</script>


<div class="container">
    <h3>Invite Code</h3>
    <p class="subheadline">Already have an invite code?</p>
    <div class="pin-wrapper">
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
    </div>
    <div class="button" style="width: 100%; max-width: 300px">Redeem Invite Code</div>
</div>

<style>
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
        text-align: center;
        gap: 6px;
    }

    input {
        width: 48px;
        height: 48px;
        text-align: center;
        font-size: 24px;
        border: 1px solid var(--darkgrey);
        -moz-appearance: textfield;
        border-radius: 8px;
    }

    input::-webkit-outer-spin-button,
    input::-webkit-inner-spin-button {
        -webkit-appearance: none;
        margin: 0;
    }

    input:focus {
        border: 1px solid var(--black);
        outline: none;
    }

    .pin-wrapper {
        display: flex;
        justify-content: space-between;
        align-items: center;
        gap: 12px;
        width: 100%;
        max-width: 300px;
        margin-top: 12px;
        margin-bottom: 6px;
    }

</style>
