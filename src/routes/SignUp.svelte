<script>
    let email = '';
    let password = '';
    let errorMessage = '';

    async function handleSubmit() {
        const res = await fetch('http://localhost:8080/api/user', {
            method: "POST",
            headers: {'Content-Type': 'application/json'},
            body: JSON.stringify({
                email,
                password
            })
        })

        if(res.ok) {
            window.location.href = '/login'
        } else if(res.status === 400) {
            errorMessage = 'Password or email is missing'
        } else if(res.status === 409) {
            errorMessage = 'Email already exist'
        }        
    }
</script>


<form on:submit|preventDefault={handleSubmit}>
    <h1>Sign up</h1>
    <input type="email" bind:value={email} placeholder="Email" />
    <input type="password" bind:value={password} placeholder="Password" />
    <button type="submit">Sign up</button>
    {#if errorMessage}
    <p class='error'>{errorMessage}</p>
    {/if}
</form>