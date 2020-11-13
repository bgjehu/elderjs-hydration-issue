<script>
  import { writable } from 'svelte/store';
  const map = writable(new Map());
  const open = key => {
    map.update(map => {
      map.set(key, {});
      return map;
    });
  };
  const close = key => {
    map.update(map => {
      map.delete(key);
      return map;
    });
  };
  const key = 'search';
  const toggle = () => {
    if ($map.has(key)) {
      close(key);
    } else {
      open(key);
    }
  };
</script>

<button type="button" on:click={toggle}>toggle</button>
{#if $map.has(key)}
  <h1>Hello!</h1>
{/if}
