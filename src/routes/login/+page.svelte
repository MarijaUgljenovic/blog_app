<script>
    let email = "";
    let password = "";
    let error = "";

    async function handleLogin(){
        const res = await fetch ('http://localhost:3000/auth/login',{

            method:'POST',
            headers: {
              'Content-Type': 'application/json'
            },
            body: JSON.stringify({
              email: email,
              password: password
           }),

            credentials: 'include'
        });

        const data = await res.json();
       
      if (res.ok) {
        
        console.log('Login success:', data);

        localStorage.setItem('token', data.token);
        window.location.href = '/dashboard';
      }else{
        error = 'Login faild. Check your credentials.';
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