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

<h1>Login</h1>

<form on:submit|preventDefault ={handleLogin}>
    <input type="email" bind:value={email} placeholder="Email" required />
    <input type="password" bind:value={password} placeholder="Password" required />
    <button type="submit">Login</button>
    {#if error}<p style="color:red">{error}</p>{/if}
</form>