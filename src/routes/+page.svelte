<script>
  import Button from "$lib/Button.svelte";

  function sayHello() {
    alert("Hello!");
  }

  function sayGoodbye() {
    alert("Goodbye!");
  }

  function saySurprise() {
    alert("Surprise 🎉");
  }
// Grocery List array
  const groceries = ["milk", "Cheer Wine", "apples", "avocado"]
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
    {#each groceryList as item}
      <li class="text-lg">{item}</li>
    {/each}
  </ul>
</div>