<script>
  import { user } from './user';

  let username;
  let password;

  function login() {
    user.auth(username, password, ({ err }) => err && alert(err));
  }

  function signup() {
    user.create(username, password, ({ err }) => {
      if (err) {
        alert(err);
      } else {
        login();
      }
    });
  }
</script>

<div class="py-5 flex flex-col h-full w-full bg-gray-700">

  <label for="username">Username</label>
  <input class="logInput" name="username" bind:value={username} minlength="3" maxlength="16" />

  <label for="password">Password</label>
  <input class="logInput" name="password" bind:value={password} type="password" />

  <br/>

  <button class="login" on:click={login}>Login</button>
  <button class="login"  on:click={signup}>Sign Up</button>
  
</div>
  