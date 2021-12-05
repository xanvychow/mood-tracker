<script>
    import Greeting from '$lib/Greeting.svelte';
    import Entry from '$lib/Entry.svelte';
    import EntryModal from '$lib/EntryModal.svelte';
    import supabase from '$lib/db';
    async function signOut() {
   	    const { error } = await supabase.auth.signOut();

   	    if (error) alert(error.message);
    };
</script>
<!-- Entries -->
<Greeting />
<section class="container px-4 py-3">
    <div class="d-flex justify-content-between">
   	 <div class="p-2">Mood Log</div>
   	 <input class="btn btn-light mb-2" type="button" onclick="myNewEntry" value="+ New Entry" data-bs-toggle="modal" data-bs-target="#newEntry" />
    </div>

    <div class="list-group mb-3">
   	 <!-- Individual Entries -->
    	<Entry />
   	 
    </div>
</section>
<!-- Sign Out -->
<section class="container px-4 py-3 text-center">
    <button class="btn btn-secondary" on:click={signOut}>Logout</button>
</section>
<EntryModal />