<script>
	import Navbar from '$lib/Navbar.svelte';
	import supabase from '$lib/db';
	import { page, session } from '$app/stores';
	import { browser } from '$app/env';
	import { goto } from '$app/navigation';
	if (browser) {
		$session = supabase.auth.session();
		redirect();
		supabase.auth.onAuthStateChange((userSession) => {
			$session = userSession;
			redirect();
		});
	}

	function redirect() {
		if ($session && $page.path === '/login') {
			goto('/');
		}
		if (!$session && $page.path === '/') {
			goto('/login');
		}
	}
	function myFunction() {
		var input, filter, ul, li, a, i, txtValue;
		input = document.getElementById('myInput');
		filter = input.value.toUpperCase();
		ul = document.getElementById('myUL');
		li = ul.getElementsByTagName('li');
		for (i = 0; i < li.length; i++) {
			a = li[i].getElementsByTagName('a')[0];
			txtValue = a.textContent || a.innerText;
			if (txtValue.toLowerCase().indexOf(filter) > -1) {
				li[i].style.display = '';
			} else {
				li[i].style.display = 'none';
			}
		}
	}

</script>

<Navbar />
<slot />
