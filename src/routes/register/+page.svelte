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

<div class="homebar">
  <a href="/" class="home-link">Home</a>
</div>

<form on:submit|preventDefault={handleRegister} class="register-form">
  <h2>Register</h2>

  <div class="form-group">
    <label for="username">Username</label>
    <input type="text" id="username" bind:value={username} name="username" placeholder="Enter your username" required />
  </div>

  <div class="form-group">
    <label for="email">Email</label>
    <input type="email" id="email" bind:value={email} name="email" placeholder="Enter your email" required />
  </div>

  <div class="form-group">
    <label for="password">Password</label>
    <input type="password" id="password" bind:value={password} name="password" placeholder="Enter your password" required />
  </div>

  <div class="form-group">
    <label for="confirmPassword">Confirm Password</label>
    <input type="password" id="confirmPassword" bind:value={confirmPassword} name="confirmPassword" placeholder="Confirm your password" required />
  </div>

  <div class="form-group">
    <label for="dob">Date of Birth</label>
    <input type="date" id="dob" bind:value={dateOfBirth} name="dob" required />
  </div>

  <div class="form-group">
    <label for="gender">Gender</label>
    <select id="gender" bind:value={gender} name="gender" required>
      <option value="" disabled selected>Select gender</option>
      <option value="male">Male</option>
      <option value="female">Female</option>
      <option value="other">Other</option>
    </select>
  </div>

  <button type="submit" class="submit-btn">Register</button>

  {#if error}
    <p class="error-message">{error}</p>
  {/if}

  {#if success}
    <p class="success-message">{success}</p>
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
    background: linear-gradient(to right, #053318, #011d0a);
    font-family: sans-serif;
    display: flex; 
    justify-content: center; 
    align-items: center; 
  }

  .register-form {
    max-width: 400px;
    padding: 20px;
    border-radius: 8px;
    background-color: #f9f9f9;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    width: 100%; 
  }

  .homebar {
    width: 100%;
    background-color: #02210f;
    padding: 1rem 2rem;
    display: flex;
    align-items: center;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
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

  h2 {
    text-align: center;
    margin-bottom: 20px;
  }

  .form-group {
    margin-bottom: 15px;
  }

  .form-group label {
    display: block;
    margin-bottom: 5px;
    font-weight: bold;
  }

  .form-group input,
  .form-group select {
    width: 100%;
    padding: 10px;
    border-radius: 4px;
    border: 1px solid #ddd;
    font-size: 14px;
  }

  .submit-btn {
    width: 100%;
    padding: 10px;
    background-color: #007bff;
    color: white;
    border: none;
    border-radius: 4px;
    font-size: 16px;
    cursor: pointer;
  }

  .submit-btn:hover {
    background-color: #0056b3;
  }

  .error-message {
    color: red;
    text-align: center;
  }

  .success-message {
    color: green;
    text-align: center;
  }
</style>