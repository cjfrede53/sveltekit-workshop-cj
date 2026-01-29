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
</script>

<div class="flex gap-4 p-8">
  <Button label="Hello" bgColor="bg-blue-500" onClick={sayHello} />
  <Button label="Goodbye" bgColor="bg-green-500" onClick={sayGoodbye} />
  <Button label="Surprise" bgColor="bg-purple-500" onClick={saySurprise} />
</div>