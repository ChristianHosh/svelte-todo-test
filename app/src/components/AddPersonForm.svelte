<script lang="ts">
    import {createEventDispatcher} from 'svelte';

    let dispatch = createEventDispatcher();

    let name: string;
    let beltColor: string;
    let age: number;

    let skills: any[] = [];

    const handleSubmit = () => {
        const person = {
            name: name,
            beltColor: beltColor,
            age: age,
            skills: skills,
            id: Math.random()
        }
        dispatch('addPerson', person);
    }
</script>

<div>
    <form on:submit|preventDefault={handleSubmit}>
        <input type="text" placeholder="Name" bind:value={name}>
        <input type="number" placeholder="Age" bind:value={age}>
        <div>
            <h2>Skills</h2>
            <label>
                <input type="checkbox" value="fighting" bind:group={skills}>
                Fighting
            </label>
            <label>
                <input type="checkbox" value="wrestling" bind:group={skills}>
                Wrestling
            </label>
            <label>
                <input type="checkbox" value="sneaking" bind:group={skills}>
                Sneaking
            </label>
        </div>
        <select bind:value={beltColor}>
            <option value="black">Black</option>
            <option value="white">White</option>
            <option value="brown">Brown</option>
            <option value="orange">Orange</option>
        </select>
        <button type="submit">Add Person</button>
    </form>
</div>

<style>
    form {
        display: flex;
        flex-direction: column;
        gap: 0.25rem;
    }

    input, select, option{
        font-size: 1.5rem;
    }

    button {
        margin-top: 0.5rem;
        font-size: 1.5rem;
    }
</style>
