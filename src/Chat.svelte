<script>
  import GUN from 'gun';
  import SEA from 'gun/sea';
  import Login from './Login.svelte';
  import ChatMessage from './ChatMessage.svelte';
  import { onMount } from 'svelte';
  import { username, user } from './user';
  import FaPaperPlane from 'svelte-icons/fa/FaPaperPlane.svelte'

  const db = GUN();

  let newMessage;
  let messages = [];

  onMount(() => {

    // Get Messages
    db.get('chat') // change for chat rooms
      .map()
      .once(async (data,id) => {
        if (data) {
          // Key for end to end encryption
          const key = '#foo'

          var message = {
            // Transform Data
            who: await db.user(data).get('alias'), // USER
            what: (await SEA.decrypt(data.what, key)) + '', // CONTENT
            when: GUN.state.is(data, 'what'), // INTERNAL TIMESTAMP
          };

          if (message.what) {
            messages = [...messages.slice(-100), message].sort((a, b => a.when - b.when));
          }
        }
      });
  });

  async function sendMessage() {
    const secret = await SEA.encrypt(newMessage, '#foo');
    const message = user.get('all').set({ what: secret });
    const index = new Date().toISOString();
    db.get('chat').get(index).put(message);
    newMessge = '';
  }
</script>

<div class="waiting-room">
  {#if $username}
  <div class="chat-room">

  <main>
    {#each messages as message (messages.when)}
      <ChatMessage {message} sender={$username}/>
    {/each}
  </main>

  <form class="msg-box" on:sumbit|preventDefault={sendMessage}>
    <input type="text" placeholder="Say Hello..." bind:value={newMessage} maxlength="150" />
    <button type="submit" disabled={!newMessage}><i class="scale-50"><FaPaperPlane/></i></button>
  </form>
  </div>

  {:else}
  <main>
    <Login/>
  </main>

  {/if}
</div>