<script>
 
</script>
<style>
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

  .profile-icon {
      width: 32px;
      height: 32px;
      border-radius: 50%;
      object-fit: cover;
      cursor: pointer;
  }

  .hero {
      width: 100vw;
      margin: 0;
      height: 100vh;
      padding: 0;
      display: flex;
      justify-content: space-between;
      align-items: center;
      background: rgb(88, 88, 85);
      overflow: hidden;
      color: white;
  }

</style>
  <div class="homebar">
    <a href="/homePage" class="home-link">Home</a>
  </div>
  <div class="hero">
    
  </div>

  <div class="top-bar">
    <a href="/profile">
      <img src="/img/profile-icon.png" alt="Profile" class="profile-icon" />
    </a>
  </div>

