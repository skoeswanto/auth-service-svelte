<script lang="ts">
  import { Link } from "svelte-routing";
</script>

<div class="min-h-screen bg-gray-100">
  <header class="bg-white shadow">
    <nav class="container mx-auto px-6 py-3">
      <div class="flex justify-between items-center">
        <div class="text-xl font-semibold text-gray-700">MedaAuth</div>
        <div>
          <Link to="/auth" class="bg-blue-500 hover:bg-blue-600 text-white font-bold py-2 px-4 rounded">
            Login / Register
          </Link>
        </div>
      </div>
    </nav>
  </header>

  <main class="container mx-auto px-6 py-8">
    <h1 class="text-4xl font-bold text-center mb-8">Welcome to MedaAuth</h1>
    <p class="text-xl text-center mb-8">
      Stop wasting time on registration and login code. Use MedaAuth for fast, easy, and secure authentication.
    </p>

    <div class="grid grid-cols-1 md:grid-cols-3 gap-8 mb-12">
      <div class="bg-white p-6 rounded-lg shadow">
        <h2 class="text-2xl font-semibold mb-4">Fast to Deploy</h2>
        <p>Get your authentication up and running in minutes, not hours.</p>
      </div>
      <div class="bg-white p-6 rounded-lg shadow">
        <h2 class="text-2xl font-semibold mb-4">Easy to Use</h2>
        <p>Simple API and SDKs make integration a breeze for developers.</p>
      </div>
      <div class="bg-white p-6 rounded-lg shadow">
        <h2 class="text-2xl font-semibold mb-4">Multi-Language Support</h2>
        <p>Supports Golang, JavaScript (Express), React, NextJS, Flutter, and React Native.</p>
      </div>
    </div>

    <h2 class="text-3xl font-bold text-center mb-8">Pricing Tiers</h2>
    <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
      <div class="bg-white p-6 rounded-lg shadow">
        <h3 class="text-2xl font-semibold mb-4">Starter</h3>
        <p class="text-3xl font-bold mb-4">$9/month</p>
        <ul class="list-disc list-inside mb-6">
          <li>Up to 1,000 active users</li>
          <li>Basic support</li>
          <li>Standard features</li>
        </ul>
        <button class="w-full bg-blue-500 hover:bg-blue-600 text-white font-bold py-2 px-4 rounded">
          Choose Plan
        </button>
      </div>
      <div class="bg-white p-6 rounded-lg shadow border-2 border-blue-500">
        <h3 class="text-2xl font-semibold mb-4">Pro</h3>
        <p class="text-3xl font-bold mb-4">$29/month</p>
        <ul class="list-disc list-inside mb-6">
          <li>Up to 10,000 active users</li>
          <li>Priority support</li>
          <li>Advanced features</li>
        </ul>
        <button class="w-full bg-blue-500 hover:bg-blue-600 text-white font-bold py-2 px-4 rounded">
          Choose Plan
        </button>
      </div>
      <div class="bg-white p-6 rounded-lg shadow">
        <h3 class="text-2xl font-semibold mb-4">Enterprise</h3>
        <p class="text-3xl font-bold mb-4">Custom</p>
        <ul class="list-disc list-inside mb-6">
          <li>Unlimited active users</li>
          <li>24/7 support</li>
          <li>Custom features</li>
        </ul>
        <button class="w-full bg-blue-500 hover:bg-blue-600 text-white font-bold py-2 px-4 rounded">
          Contact Sales
        </button>
      </div>
    </div>
  </main>
</div>