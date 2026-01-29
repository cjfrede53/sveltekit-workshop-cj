<script>
  import Button from "$lib/Button.svelte";
  import { onMount } from "svelte";

  function sayHello() {
    alert("Hello!");
  }

  function sayGoodbye() {
    alert("Goodbye!");
  }

  function saySurprise() {
    alert("Surprise 🎉");
  }

  // Task 2: Grocery list array
  const groceries = ["milk", "Cheer Wine", "apples", "avocado"];

  // Task 3: API state
  let loading = true;
  let error = "";
  let drinks = [];

  onMount(async () => {
    loading = true;
    error = "";

    try {
      const res = await fetch(
        "https://www.thecocktaildb.com/api/json/v1/1/filter.php?i=Bourbon"
      );

      if (!res.ok) {
        throw new Error(`Request failed: ${res.status}`);
      }

      const data = await res.json();
      drinks = data?.drinks ?? [];
    } catch (e) {
      error = e instanceof Error ? e.message : "Something went wrong while fetching drinks.";
      drinks = [];
    } finally {
      loading = false;
    }
  });
</script>



<div class="flex gap-4 p-8">
  <Button label="Hello" bgColor="bg-blue-500" onClick={sayHello} />
  <Button label="Goodbye" bgColor="bg-green-500" onClick={sayGoodbye} />
  <Button label="Surprise" bgColor="bg-purple-500" onClick={saySurprise} />
</div>
<!-- Task 2: Grocery list rendered with {#each} -->

<div class="p-8">
  <h2 class="text-2xl font-bold mb-4">Grocery List</h2> 
<!-- mb creates a header via tailwind -->
  <ul class="list-disc pl-6 space-y-2">
    {#each groceries as item}
      <li class="text-lg">{item}</li>
    {/each}
  </ul>


  <!-- Task 3 -->
  <section>
    <h2 class="text-2xl font-bold mb-4">Task 3: Whiskey Drinks Menu</h2>

    {#if loading}
      <p class="text-gray-600">Loading drinks...</p>
    {:else if error}
      <p class="text-red-600">Error: {error}</p>
    {:else if drinks.length === 0}
      <p class="text-gray-600">No drinks found.</p>
    {:else}
      <ul class="list-disc pl-6 space-y-2">
        {#each drinks as drink}
          <li class="text-lg">{drink.strDrink}</li>
        {/each}
      </ul>
    {/if}
  </section>
</div>