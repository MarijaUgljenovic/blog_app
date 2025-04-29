
<style>

    * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
    }

    

    .homebar {
        width: 100%;
        background-color: #02210f;  /* ili neka boja po izboru */
        padding: 1rem 2rem;
        display: flex;
        align-items: center;
        box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
        position: fixed;   /* ako želiš da ostane fiksiran pri skrolu */
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

    .top-bar {
        position: fixed;
        top: 1rem;
        right: 1rem;
        display: flex;
        gap: 1.5rem;
        z-index: 1000;
    }

    .text-button {
        background: none;
        border: none;
        color: #e9e4ee;
        font-size: 1.1rem;
        cursor: pointer;
        text-decoration: none;
        font-weight: 600;
    }

    .text-button:hover {
        text-decoration: underline;
    }

    .hero {
        width: 100%;
        margin: 0;
        padding: 0;
        overflow: hidden;
        display: flex;
        flex-direction: row; 
        justify-content: space-between;
        align-items: center;
        height: auto;
        background: linear-gradient(to right, #053318, #011d0a);
        color: white;
        text-align: left;
   }

    .hero-text {
        flex: 1;
    }

    .hero-image {
        flex: 1;
        display: flex;
        justify-content: flex-end;
        align-items: flex-start;
    }

    .hero-image img {
        max-width: 100%;
        height: auto;
        border-radius: 1rem;
        display: block;
        object-fit: contain;
    }

    .text-button:hover {
        text-decoration: underline;
    }

    h1 {
        font-size: 3rem;
        margin-bottom: 1rem;
    }
  
    p {
        font-size: 1.2rem;
        max-width: 600px;
        margin-bottom: 2rem;
    }
  
  </style>

<div class="homebar">
    <a href="/" class="home-link">Home</a>
</div>

<div class="top-bar">
    <a href="/login" class="text-button">Login</a>
    <a href="/register" class="text-button">Register</a>
</div>
  
  
  <div class="hero">
    <div class="hero-text">
      <h1>Welcome!</h1>
      <p>Create your style.</p>
    </div>
    <div class="hero-image">
      <img src="/img/img1.jpg" alt="nature" />
    </div>
  </div>