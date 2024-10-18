<script lang="ts">
  import { Pie } from 'svelte-chartjs';
  import { Chart as ChartJS, Title, Tooltip, Legend, ArcElement, CategoryScale } from 'chart.js';
  import PlusCircle from 'svelte-icons/fa/FaPlusCircle.svelte';
  import Sync from 'svelte-icons/fa/FaSync.svelte';

  ChartJS.register(Title, Tooltip, Legend, ArcElement, CategoryScale);

  let apps = [
    { id: 1, name: 'App 1', apiKey: 'key1', apiSecret: 'secret1', apiCalls: 1000 },
    { id: 2, name: 'App 2', apiKey: 'key2', apiSecret: 'secret2', apiCalls: 2000 },
  ];

  let selectedApp = null;

  const chartData = {
    labels: ['App 1', 'App 2'],
    datasets: [{
      data: [1000, 2000],
      backgroundColor: ['#FF6384', '#36A2EB'],
      hoverBackgroundColor: ['#FF6384', '#36A2EB']
    }]
  };

  function createNewApp() {
    // Logic to create a new app
    console.log('Creating new app');
  }

  function regenerateApiSecret(app) {
    // Logic to regenerate API secret
    console.log('Regenerating API secret for', app.name);
  }

  function selectApp(app) {
    selectedApp = app;
  }
</script>

<div class="min-h-screen bg-gray-100">
  <header class="bg-white shadow">
    <div class="container mx-auto px-6 py-3">
      <h1 class="text-2xl font-semibold text-gray-800">MedaAuth Dashboard</h1>
    </div>
  </header>

  <main class="container mx-auto px-6 py-8">
    <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
      <div class="col-span-2">
        <div class="bg-white p-6 rounded-lg shadow mb-8">
          <h2 class="text-xl font-semibold mb-4">Your Apps</h2>
          <button on:click={createNewApp} class="bg-green-500 hover:bg-green-600 text-white font-bold py-2 px-4 rounded mb-4 flex items-center">
            <div class="w-4 h-4 mr-2"><PlusCircle /></div> Create New App
          </button>
          <table class="w-full">
            <thead>
              <tr>
                <th class="text-left">Name</th>
                <th class="text-left">API Key</th>
                <th class="text-left">API Calls</th>
                <th class="text-left">Actions</th>
              </tr>
            </thead>
            <tbody>
              {#each apps as app}
                <tr>
                  <td>{app.name}</td>
                  <td>{app.apiKey}</td>
                  <td>{app.apiCalls}</td>
                  <td>
                    <button on:click={() => selectApp(app)} class="text-blue-500 hover:text-blue-700 mr-2">View</button>
                    <button on:click={() => regenerateApiSecret(app)} class="text-green-500 hover:text-green-700 flex items-center">
                      <div class="w-4 h-4 mr-1"><Sync /></div> Regenerate Secret
                    </button>
                  </td>
                </tr>
              {/each}
            </tbody>
          </table>
        </div>

        {#if selectedApp}
          <div class="bg-white p-6 rounded-lg shadow">
            <h2 class="text-xl font-semibold mb-4">{selectedApp.name} Details</h2>
            <p><strong>API Key:</strong> {selectedApp.apiKey}</p>
            <p><strong>API Secret:</strong> {selectedApp.apiSecret}</p>
            <p><strong>API Calls:</strong> {selectedApp.apiCalls}</p>
            <h3 class="text-lg font-semibold mt-4 mb-2">Settings</h3>
            <div class="mb-2">
              <label class="inline-flex items-center">
                <input type="checkbox" class="form-checkbox" checked>
                <span class="ml-2">Can create new user</span>
              </label>
            </div>
            <div class="mb-2">
              <label class="inline-flex items-center">
                <input type="checkbox" class="form-checkbox" checked>
                <span class="ml-2">Use state</span>
              </label>
            </div>
            <div class="mb-2">
              <label class="inline-flex items-center">
                <input type="checkbox" class="form-checkbox" checked>
                <span class="ml-2">Use PKCE</span>
              </label>
            </div>
            <div class="mt-4">
              <label class="block text-gray-700 text-sm font-bold mb-2" for="otpMethod">
                OTP Method
              </label>
              <select id="otpMethod" class="form-select mt-1 block w-full">
                <option>Email</option>
                <option>FazPass</option>
              </select>
            </div>
          </div>
        {/if}
      </div>

      <div>
        <div class="bg-white p-6 rounded-lg shadow mb-8">
          <h2 class="text-xl font-semibold mb-4">API Calls Distribution</h2>
          <Pie data={chartData} options={{ responsive: true }} />
        </div>

        <div class="bg-white p-6 rounded-lg shadow">
          <h2 class="text-xl font-semibold mb-4">Quick Stats</h2>
          <p><strong>Total Apps:</strong> {apps.length}</p>
          <p><strong>Total API Calls:</strong> {apps.reduce((sum, app) => sum + app.apiCalls, 0)}</p>
        </div>
      </div>
    </div>
  </main>
</div>