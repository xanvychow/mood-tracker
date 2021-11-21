<script>
    import Greeting from '$lib/Greeting.svelte';
    import Entry from '$lib/Entry.svelte';
    function myNewEntry() {
        var element = document.createElement("Entry");
        document.body.appendChild(element);
    }
    function myNewEntry() {
        var newEntry = document.createElement("Entry");
        document.getElementById("entryHere").appendChild(newEntry);
    }
</script>
<!-- Entries -->
<section class="container px-4 py-3">
    <div class="d-flex justify-content-between">
   	 <div class="p-2">Mood Log</div>
   	 <input class="btn btn-light mb-2" type="button" onclick="myNewEntry" value="+ New Entry" />
    </div>

    <div class="list-group mb-3" id="entryHere">
   	 <!-- Individual Entries -->
    	<Entry />
   	 
    </div>
</section>