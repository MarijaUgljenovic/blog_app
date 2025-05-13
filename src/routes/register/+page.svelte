<script>
  import { goto } from '$app/navigation';
  let username = "";
  let email = "";
  let password = "";
  let confirmPassword = "";
  let dateOfBirth = "";
  let usernameError = "";
  let emailError = "";
  let passwordError = "";
  let confirmPasswordError = "";
  let gender = "";
  let error = "";
  let success = "";

  async function handleRegister() {
    error = "";
    success = "";
    let hasError = false;

    const passwordRegex = /^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[^A-Za-z0-9]).{8,}$/;
    if (!passwordRegex.test(password)) {
      error = "Password must be at least 8 characters long and include at least one uppercase letter, one lowercase letter, one number, and one special character.";
      hasError = true;
      hasError = true;
    }

    if (password !== confirmPassword) {
      error = "Passwords do not match.";
      hasError = true;
    }

    const emailRegex = /^[a-zA-Z0-9]+(\.[a-zA-Z0-9]+)?@gmail\.com$/;
    if (!emailRegex.test(email)) {
      error = 'Email must be in the form of "name@gmail.com" or "name.name@gmail.com".';
      hasError = true;
    }

    const usernameRegex = /^[a-z0-9._]+$/;
    if (!usernameRegex.test(username)) {
      error = "Username can only contain lowercase letters, numbers, dots (.) and underscores (_).";
      hasError = true;
    }

    if (hasError) return;



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
<div class="background-image"></div>
<div class="background-overlay"></div>

<div class="homebar">
  <a href="/" class="home-link">Home</a>
</div>

<form on:submit|preventDefault={handleRegister} class="register-form">
  <h2>Register</h2>

  <div class="form-group">
    <label for="username">Username</label>
    <input type="text" id="username" bind:value={username} required />
    {#if usernameError}
      <p class="field-error">{usernameError}</p>
    {/if}
  </div>

  <div class="form-group">
    <label for="email">Email</label>
    <input type="text" id="email" bind:value={email} required />
    {#if emailError}
      <p class="field-error">{emailError}</p>
    {/if}  
  </div>

  <div class="form-group">
    <label for="password">Password</label>
    <input type="text" id="password" bind:value={password} required />
    {#if passwordError}
      <p class="field-error">{passwordError}</p>
    {/if}    
  </div>

  <div class="form-group">
    <label for="confirmPassword">Confirm Password</label>
    <input type="text" id="confirmPassword" bind:value={confirmPassword} required />
    {#if confirmPasswordError}
      <p class="field-error">{confirmPasswordError}</p>
    {/if}   
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
   
    font-family: sans-serif;
    display: flex; 
    justify-content: center; 
    align-items: center; 
  }

  .background-image {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background-image: url('/img/poz3.jpg');
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  background-attachment: fixed;
  z-index: -20;
}

.background-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background-color: rgba(0, 0, 0, 0.5);
  z-index: -10;
}

  .field-error {
    color: red;
    font-size: 0.9rem;
    margin-top: 5px;
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
    background-color: 353333;
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
  }

  .success-message {
    color: green;
    text-align: center;
  }
</style>