<script>
  import PokiBtn from './components/PokiBtn.svelte'
  import {username,user} from './user.js'

  function signout() {
    user.leave();
    username.set('');
  }

</script>

<header class="headerUI">
  <div class="my-auto">
    <i><PokiBtn/></i>
  </div>

  {#if $username}

    <div class="my-user">
      <img src={`https://avatars.dicebear.com/api/initials/${$username}.svg`} alt="avatar" /> 
      <button class="px-2">{$username}</button>
    </div>

    <button class="signout-button" on:click={signout}>
      Log Out
    </button>

  {:else}
    <h3 class="my-auto">POKI DApp</h3>
  {/if}
  
</header>

