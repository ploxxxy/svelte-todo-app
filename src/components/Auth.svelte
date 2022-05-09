<script>
    import { supabase } from '../supabase'

    let loading = false
    let email

    const handleLogin = async () => {

        try {
            loading = true
            await supabase.auth.signIn({ provider: 'discord' })
        } catch (error) {
            console.error(error)
            alert(error.error_description || error.message)
        } finally {
            loading = false
        }

        // try {
        //     loading = true
        //     await supabase.auth.signIn({email})
        //     alert('Check your email for the login link')
        // } catch (error) {
        //     console.error(error)
        //     alert(error.error_description || error.message)
        // } finally {
        //     loading = false
        // }
    }

</script>

<h1 class="text-2xl font-bold text-center text-gray-800 md:text-3xl">Log In</h1>
<p class="text-center mt-2">Sign in via magic link</p>

<form on:submit|preventDefault={handleLogin}>
    <div class="flex flex-col text-sm mb-2">
        <label class="font-bold mb-2 text-gray-800" for="email">Email</label>
        <input class="appearance-none shadow-sm border border-gray-200 p-2 focus:outline-none focus:border-gray-500 rounded-lg" type="email" name="email" placeholder="Your email" bind:value={email}>
    </div>
    <button class="w-full shadow-sm rounded bg-blue-600 hover:bg-blue-700 text-white py-2 px-4" type="submit">Log In</button>
</form>