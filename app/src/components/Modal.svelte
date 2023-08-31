<script lang="ts">
    export let showModal: boolean = true;
    const hideModal = () => {
        showModal = false;
    }
</script>

{#if showModal}
    <div class="backdrop" on:click|self={hideModal} role="doc-cover">
        <div class="modal-container">
            <slot></slot>
        </div>
    </div>
{/if}

<style>
    .backdrop {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: rgba(0, 0, 0, 0.8);

        display: flex;
    }

    .modal-container {
        background-color: white;
        max-width: 40%;
        max-height: 40%;
        border-radius: 1rem;
        padding: 2rem;

        display: flex;
        flex-direction: column;
        gap: 0.25rem;

        margin: auto auto;

        text-align: center;
    }

    .promo {
        background-color: lightblue;
    }
</style>