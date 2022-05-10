<script>
  import FaBomb from 'svelte-icons/fa/FaBomb.svelte'
  import PokiBtn from './PokiBtn.svelte'
</script>

<div class="h-full w-16 flex flex-col bg-gray-900 text-white shadow-lg">
  <PokiBtn/>
  <div class="sidebar-icon group">
    <p>[p]</p>
    <div class="sidebar-tooltip group-hover:scale-100"><p>pok</p></div>
  </div>
  <div class="sidebar-icon group">
    <p>[a]</p>
    <div class="sidebar-tooltip group-hover:scale-100"><p>pok</p></div>
  </div>
  <div class="sidebar-icon group">
    <p>[v]</p>
    <div class="sidebar-tooltip group-hover:scale-100"><p>pok</p></div>
  </div>
  <div class="sidebar-icon group">
    <p>[s]</p>
    <div class="sidebar-tooltip group-hover:scale-100"><p>pok</p></div>
  </div>
</div>