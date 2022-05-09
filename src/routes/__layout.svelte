<script>
	import { supabase } from '../supabase'
	import '../app.css'
	import Auth from '../components/Auth.svelte'
	import { user } from '../store/authStore'
	import { loadTodos } from '../store/todoStore'
	import Navbar from '../components/Navbar.svelte'

	user.set(supabase.auth.user())

	supabase.auth.onAuthStateChange((_, session) => {
		user.set(session?.user)
		if (session?.user) {
			loadTodos()
		}
	})
</script>

<div class="container mx-auto my-6 max-w-lg">
	{#if $user}
		<Navbar />
		<slot />
	{:else}
		<Auth />
	{/if}
</div>
