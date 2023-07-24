<script lang="ts">
  import Fullscreen from 'svelte-fullscreen';

  const colors = ['white', 'black', 'red', 'green', 'blue'];
  let colorIndex = 0;

  const handleClick = (onRequest: () => void) => {
    onRequest();
    colorIndex = (colorIndex + 1) % 5;
  };
</script>

<main>
  <Fullscreen let:onRequest>
    <div
      role="button"
      tabindex="0"
      class="bg"
      style="--bg-color: {colors[colorIndex]}"
      on:click={() => handleClick(onRequest)}
      on:keypress={() => handleClick(onRequest)}
    />
  </Fullscreen>
</main>

<style>
  .bg {
    height: 100vh;
    width: 100vw;
    background-color: var(--bg-color);
    cursor: pointer;
  }
</style>
