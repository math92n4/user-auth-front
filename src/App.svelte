<script>
  import { Router, Route } from 'svelte-routing';
  import Login from './routes/Login.svelte';
  import SignUp from './routes/SignUp.svelte';
  import LoggedIn from './routes/LoggedIn.svelte';
  import Nav from './components/Nav.svelte'
</script>

<Nav />

<Router>
  <Route path="/login" component={Login} />
  <Route path="/signup" component={SignUp} />
  <Route path="/loggedin" component={LoggedIn} />
</Router>




