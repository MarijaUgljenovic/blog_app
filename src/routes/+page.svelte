<script>
</script>
  
  <style>
    /* GLOBALNI RESET */
    :global(*) {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
    }
  
    :global(html), :global(body) {
        width: 100%;
        overflow-x: hidden;
        background-color: #011d0a;
        font-family: sans-serif;
       
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
  
    .top-bar {
        position: fixed;
        top: 1rem;
        right: 1.5rem;
        display: flex;
        gap: 1.5rem;
        z-index: 1001;
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
        width: 100vw;
        margin: 0;
        height: 100vh;
        padding: 0;
        display: flex;
        justify-content: space-between;
        align-items: center;
        background: rgb(4, 44, 34);
        overflow: hidden;
        color: white;
    }
  
    .hero-text {
        margin-left: 6vw;
        flex: 1;
    }
  
    .hero-image {
        flex: 1;
        display: flex;
        justify-content: flex-end;
        align-items: center;
    }
  
    .hero-image img {
        max-width: 100%;
        height: auto;
        border-radius: 1rem;
        display: block;
        object-fit: contain;

        /* Mek prelaz na levoj ivici slike */
        -webkit-mask-image: linear-gradient(to right, rgba(0, 0, 0, 0) 0%, rgba(0, 0, 0, 0.4) 10%, rgba(0, 0, 0, 0.8) 20%, rgba(0, 0, 0, 1) 30%);
        mask-image: linear-gradient(to right, rgba(0, 0, 0, 0) 0%, rgba(0, 0, 0, 0.4) 10%, rgba(0, 0, 0, 0.8) 20%, rgba(0, 0, 0, 1) 30%);

        opacity: 0;
        transform: translateX(30px);
        animation: fadeInSmooth 1.2s ease-out forwards;
    }
  
    @keyframes fadeInSmooth {
        to {
            opacity: 1;
            transform: translateX(0);
        }
    }

    @keyframes fadeInMask {
    0% {
        -webkit-mask-image: linear-gradient(to right, transparent 0%, black 0%);
        mask-image: linear-gradient(to right, transparent 0%, black 0%);
        opacity: 0;
        transform: translateX(30px);
    }
    100% {
        -webkit-mask-image: linear-gradient(to right, transparent 0%, black 15%);
        mask-image: linear-gradient(to right, transparent 0%, black 15%);
        opacity: 1;
        transform: translateX(0);
    }
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
  
  <!-- HTML -->
  <div class="homebar">
        <a href="/" class="home-link">Home</a>
  </div>
  
  <div class="top-bar">
        <a href="/login" class="text-button">Login</a>
        <a href="/register" class="text-button">Register</a>
  </div>
  
  <div class="hero">
        <div class="hero-text">
            <h1>OnePlace</h1>
            <p>Explore your path.</p>
        </div>
            <div class="hero-image">
            <img src="/img/img6.jpg" alt="nature" />
        </div>
  </div>
  