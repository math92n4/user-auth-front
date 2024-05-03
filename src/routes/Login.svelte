<script>
    let email = '';
    let password = '';
    let errorMessage = ''

    async function handleSubmit() {
        const res = await fetch('http://localhost:8080/api/login', {
            method: "POST",
            headers: {'Content-Type': 'application/json'},
            credentials: 'include',
            body: JSON.stringify({
                email,
                password
            })
        })

        if(res.ok) {
            window.location.href = '/loggedin'
        } else {
            errorMessage = 'Bad credentials, try again'
        }
    }
</script>


<form on:submit|preventDefault={handleSubmit}>
    <h1>Log in</h1>
    <input type="email" bind:value={email} placeholder="Email" />
    <input type="password" bind:value={password} placeholder="Password" />
    <button type="submit">Log in</button>
    {#if errorMessage}
    <p class='error'>{errorMessage}</p>
    {/if}
</form>
