<script>
  import { goto } from '$app/navigation';
  let email = "";
  let password = "";
  let error = "";

  async function handleLogin() {
    const res = await fetch('http://localhost:3000/auth/login', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json'
      },
      body: JSON.stringify({
        email: email,
        password: password
      }),
      credentials: 'include'
    });

    if (res.ok) {
      const data = await res.json(); 
      console.log('Login success:', data);

      localStorage.setItem('token', data.token);
      goto('/homePage');
    } else if (res.status === 403) {
        error = 'Wrong password.';
    } else if (res.status === 400) {
        error = 'Missing or invalid credentials.';
    } else {
        error = 'Login failed. Please try again.';
    }
  }
</script>

<div class="homebar">
  <a href="/" class="home-link">Home</a>
</div>

<form on:submit|preventDefault={handleLogin} class="login-form">
  <div class="form-group">
    <label for="email">Email</label>
    <input type="email" id="email" bind:value={email} placeholder="Enter your email" required />
  </div>

  <div class="form-group">
    <label for="password">Password</label>
    <input type="password" id="password" bind:value={password} placeholder="Enter your password" required />
  </div>

  <button type="submit" class="submit-btn">Login</button>

  {#if error}
    <p class="error-message">{error}</p>
  {/if}
</form>


<style>
 
:global(*) {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

:global(html), :global(body) {
    width: 100%;
    height: 100%; 
    overflow-x: hidden;
    
    font-family: sans-serif;
    display: flex; 
    justify-content: center; 
    align-items: center; 
}

.homebar {
    width: 100%;
    background-color: #1f1e1e;
    padding: 1rem 2rem;
    display: flex;
    align-items: center;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
    position: fixed;
    top: 0;
    left: 0;
    z-index: 1000;
}
  
  .home-link {
      color: #e9e4ee;
      text-decoration: none;
      font-size: 1.2rem;
      font-weight: bold;
  }

  .home-link:hover {
      text-decoration: underline;
  }


.login-form {
    max-width: 400px;
    padding: 20px;
    border-radius: 8px;
    background-color: #f9f9f9;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    width: 100%; /* Omogućava formi da se širi do maksimalne širine */
}

.form-group {
    margin-bottom: 15px;
}

.form-group label {
    display: block;
    margin-bottom: 5px;
    font-weight: bold;
}

.form-group input {
    width: 100%;
    padding: 10px;
    border-radius: 4px;
    border: 1px solid #ddd;
    font-size: 14px;
}

.submit-btn {
    width: 100%;
    padding: 10px;
    background-color: #1f1e1e;
    color: white;
    border: none;
    border-radius: 4px;
    font-size: 16px;
    cursor: pointer;
}

.submit-btn:hover {
    background-color: #302e2e;
}

.error-message {
    color: red;
    text-align: center;
    margin-top: 10px;
}


.hero {
      width: 100vw;
      margin: 0;
      height: 100vh;
      padding: 0;
      display: flex;
      justify-content: space-between;
      align-items: center;
      background: rgb(102, 137, 138);
      overflow: hidden;
      color: white;
  }

</style>