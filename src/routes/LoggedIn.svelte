<script>
    import { onMount } from 'svelte'
    import { authenticated } from '../stores/auth.js';

    let message = ''

    onMount(async () => {
        
        const res = await fetch('http://localhost:8080/api/user', {
        headers: {'Content-Type': 'application/json'},
        credentials: 'include'
    })
            
    if(!res.ok) {
        window.location.href = "/login"
    }

    const content = await res.json()
        
    message = `User ${content.email} is now logged on`
    authenticated.set(true);
}) 

</script>


<div class="video-container">
    <h2>{message}</h2>
    <h2>Your JWT token has been created</h2>
    <iframe width="500" height="500" id="video" title='title' src="https://www.youtube.com/embed/DLzxrzFCyOs?hl=en_US&version=3&rel=0&autoplay=1" frameborder="1" allow="autoplay" allowfullscreen></iframe>
</div>
