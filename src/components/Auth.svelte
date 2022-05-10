<script>
    import { supabase } from '../supabase'

    let loading = false
    let email

    const handleLogin = async (provider) => {

        try {
            loading = true
            await supabase.auth.signIn({ provider: provider }, { redirectTo: window.location.origin })
        } catch (error) {
            console.error(error)
            alert(error.error_description || error.message)
        } finally {
            loading = false
        }

    }

</script>

<div class="flex flex-col items-center justify-center h-screen">
    <p class="text-2xl my-4">Sign in via:</p>
            <button class="btn btn-wide my-1 btn-primary" type="submit" on:click|preventDefault={() => handleLogin('discord')}>Discord</button>
            <button class="btn btn-wide my-1 btn-primary btn-disabled" type="submit">Github</button>
            <button class="btn btn-wide my-1 btn-primary btn-disabled" type="submit">Google</button>
            <button class="btn btn-wide my-1 btn-primary btn-disabled" type="submit">Twitter</button>
</div>