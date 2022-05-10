<script>
  import Header from '../Header.svelte';
  import Chat from '../Chat.svelte';
  import LeftUi from '../components/LeftUI.svelte';
</script>

<div class="app">
  <Header/>
  <div class="flex flex-row h-full">
    <LeftUi/>
    <Chat/>
  </div>
</div>