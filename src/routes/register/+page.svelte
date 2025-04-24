<script>

    import { goto } from '$app/navigation';
    let username = "";
    let email = "";
    let password = "";
    let confirmPassword = "";
    let dateOfBirth = "";
    let gender = "";
    let error = "";
    let success = "";
  
    async function handleRegister() {
      if (password !== confirmPassword) {
        error = "Passwords do not match.";
        return;
      }
  
      const res = await fetch('http://localhost:3000/auth/register', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json'
        },
        body: JSON.stringify({
          email,
          username,
          password,
          dateOfBirth,
          gender
        }),
        credentials: 'include'
      });
  
      const data = await res.json();
  
      if (res.ok) {
        success = "Registration successful!";
        goto('/login');
        
      } else {
        error = data.message || "Registration failed.";
      }
    }
  </script>
  
  <form on:submit|preventDefault={handleRegister}>
    <input type="text" bind:value={username} placeholder="Username" required />
    <input type="email" bind:value={email} placeholder="Email" required />
    <input type="password" bind:value={password} placeholder="Password" required />
    <input type="password" bind:value={confirmPassword} placeholder="Confirm Password" required />
    <input type="date" bind:value={dateOfBirth} required />
    
    <select bind:value={gender} required>
      <option value="" disabled selected>Select gender</option>
      <option value="male">Male</option>
      <option value="female">Female</option>
      <option value="other">Other</option>
    </select>
  
    <button type="submit">Register</button>
    {#if error}<p style="color:red">{error}</p>{/if}
    {#if success}<p style="color:green">{success}</p>{/if}
  </form>
  