<script lang="ts">
  import { createForm } from "svelte-forms-lib";
  import * as yup from "yup";
  import { navigate } from "svelte-routing";

  let isRegistering = true;

  const { form, errors, handleChange, handleSubmit } = createForm({
    initialValues: {
      countryCode: "",
      phoneNumber: "",
      password: "",
    },
    validationSchema: yup.object().shape({
      countryCode: yup.string().required("Country code is required"),
      phoneNumber: yup.string().required("Phone number is required"),
      password: yup.string().required("Password is required").min(8, "Password must be at least 8 characters"),
    }),
    onSubmit: (values) => {
      console.log(values);
      // Here you would typically make an API call to register or login
      // For this example, we'll just navigate to the dashboard
      navigate("/dashboard");
    },
  });

  function toggleMode() {
    isRegistering = !isRegistering;
  }
</script>

<div class="min-h-screen flex items-center justify-center bg-gray-100">
  <div class="bg-white p-8 rounded-lg shadow-md w-full max-w-md">
    <h2 class="text-2xl font-bold mb-6 text-center">
      {isRegistering ? "Register" : "Login"} to MedaAuth
    </h2>
    <form on:submit={handleSubmit}>
      <div class="mb-4">
        <label for="countryCode" class="block text-gray-700 text-sm font-bold mb-2">Country Code</label>
        <input
          type="text"
          id="countryCode"
          name="countryCode"
          class="w-full px-3 py-2 border rounded-lg"
          on:change={handleChange}
          value={$form.countryCode}
        />
        {#if $errors.countryCode}
          <p class="text-red-500 text-xs italic">{$errors.countryCode}</p>
        {/if}
      </div>
      <div class="mb-4">
        <label for="phoneNumber" class="block text-gray-700 text-sm font-bold mb-2">Phone Number</label>
        <input
          type="tel"
          id="phoneNumber"
          name="phoneNumber"
          class="w-full px-3 py-2 border rounded-lg"
          on:change={handleChange}
          value={$form.phoneNumber}
        />
        {#if $errors.phoneNumber}
          <p class="text-red-500 text-xs italic">{$errors.phoneNumber}</p>
        {/if}
      </div>
      <div class="mb-6">
        <label for="password" class="block text-gray-700 text-sm font-bold mb-2">Password</label>
        <input
          type="password"
          id="password"
          name="password"
          class="w-full px-3 py-2 border rounded-lg"
          on:change={handleChange}
          value={$form.password}
        />
        {#if $errors.password}
          <p class="text-red-500 text-xs italic">{$errors.password}</p>
        {/if}
      </div>
      <div class="flex items-center justify-between">
        <button
          type="submit"
          class="bg-blue-500 hover:bg-blue-600 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
        >
          {isRegistering ? "Register" : "Login"}
        </button>
        <button
          type="button"
          on:click={toggleMode}
          class="inline-block align-baseline font-bold text-sm text-blue-500 hover:text-blue-800"
        >
          {isRegistering ? "Switch to Login" : "Switch to Register"}
        </button>
      </div>
    </form>
  </div>
</div>