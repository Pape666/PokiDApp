<script>
  import FaBomb from 'svelte-icons/fa/FaBomb.svelte'

  let count = 0;

  function addOne() {
    count += 1;
  }
</script>


<div class="poki-icon group">
  <button class="scale-50" on:click={addOne}>
    <FaBomb/>
  </button>
  <div class="poki-tooltip group-hover:scale-100"><p>{count}</p></div>
</div>