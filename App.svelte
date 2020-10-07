<script>
    import Entry from './Entry.svelte';
    import { slide } from "svelte/transition";

    let entries = [];

    function addEntry() {
        entries.push({ unique_id: Date.now(), message: "HERE I AM" });
        if (entries.length > 4) {
            entries.shift();
        }
        entries=entries;
    }
</script>

<style>
    .col {
        width: 200px;
        margin-right: 20px;
        border: 1px solid black;
        height: 300px;
        display: inline-block;
    }
</style>

<button on:click={addEntry}>Add</button>

<div>
    <div class="col">
    {#each entries.reverse() as entry (entry.unique_id)}
        <div transition:slide>
            <Entry {entry} />
        </div>
    {/each}
    </div>

    <div class="col">
    {#each entries.reverse() as entry}
        <div transition:slide>
            <Entry {entry} />
        </div>
    {/each}
    </div>
</div>
