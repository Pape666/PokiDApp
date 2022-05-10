<script>
  import FaLock from 'svelte-icons/fa/FaLock.svelte'
  import { username, user } from '../user';
</script>

<div class="flex flex-col w-64 bg-gray-800 border-r-2 border-gray-900 border-solid">
{#if $username}
<main>
  <div class="py-2 h-auto border-solid border-b-2 border-gray-900">
    <h2>PUBLIC BOARDS</h2>
    <div class="channel-card"># general</div>
    <div class="channel-card"># music</div>
    <div class="channel-card"># movies</div>
    <div class="channel-card"># private</div>
  </div>

  <div class="py-2 h-3/4">
    <h2>PRIVATE CHAT</h2>
    <div class="user-card"></div>
    <div class="user-card"></div>
    <div class="user-card"></div>
    <div class="user-card"></div>
  </div>
</main>
{:else}
<main>

  <div class="flex">
    <div class="lock-icon">
      <FaLock/>
    </div>
  </div>


</main>
{/if}
</div>
