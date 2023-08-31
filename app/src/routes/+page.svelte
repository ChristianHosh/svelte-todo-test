<script lang="ts">
    import Modal from "../components/Modal.svelte";
    import AddPersonForm from "../components/AddPersonForm.svelte";

    let showModal: boolean = false;

    let people = [
        {name: "Christian Hosh", beltColor: "Black", age: 21, id: 1},
        {name: "John Doe", beltColor: "Orange", age: 24, id: 2},
        {name: "Rami Abu Ayash", beltColor: "White", age: 20, id: 3},
    ]

    const deletePersonById = (event: Event, id: number) => {
        people = people.filter((person) => person.id !== id);
    }

    const toggleModal = () => {
        showModal = !showModal;
    }

    const addPerson = (event: CustomEvent) => {
        console.log("ADDING", event.detail);
        const person = event.detail;

        people = [person, ...people];
    }

</script>

<Modal {showModal} on:click={toggleModal}>
    <AddPersonForm on:addPerson={(e) => {
        toggleModal();
        addPerson(e)
    }}/>
</Modal>

<main>
    <button type="button" on:click={toggleModal}>Add New Person</button>

    {#each people as person (person.id)}
        <div class="card">
            <h4>{person.name}</h4>
            <p>{person.age} years old, {person.beltColor} Belt</p>
            <button on:click={(event) => deletePersonById(event, person.id)}>Delete</button>
        </div>
    {:else}
        <div>There are no people to show</div>
    {/each}
</main>


<style>
    main {
        padding: 1rem 0.5rem;
    }

    .card {
        border-bottom: 1px solid rgb(128, 128, 128);
        padding: 0.25rem;
    }

    h4, p {
        text-transform: capitalize;
    }

</style>

