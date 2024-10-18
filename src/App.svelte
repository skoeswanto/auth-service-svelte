<script lang="ts">
  import { Router, Route } from "svelte-routing";
  import LandingPage from "./routes/LandingPage.svelte";
  import RegisterLogin from "./routes/RegisterLogin.svelte";
  import Dashboard from "./routes/Dashboard.svelte";

  export let url = "";
</script>

<Router {url}>
  <main>
    <Route path="/" component={LandingPage} />
    <Route path="/auth" component={RegisterLogin} />
    <Route path="/dashboard" component={Dashboard} />
  </main>
</Router>