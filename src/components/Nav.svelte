<script>
    import { authenticated } from "../stores/auth"
    let auth = false;
    authenticated.subscribe(a => auth = a)

    async function logOut() {
        const res = await fetch('http://localhost:8080/api/logout', {
            method:'POST',
            headers: {'Content-Type': 'application/json'},
            credentials: 'include'
        })

        if(res.ok) {
            window.location.href = '/'
        }
    }

</script>

{#if auth}
<nav class="navbar">
    <ul class="navbar-links">
        <li><a href="/login">Logout</a></li>
    </ul>
</nav>

{:else }
<nav class="navbar">
    <ul class="navbar-links">
        <li><a href="/login">Login</a></li>
        <li><a href="/signup">Sign up</a></li>
    </ul>
</nav>
{/if}

