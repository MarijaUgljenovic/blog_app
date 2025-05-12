
<script>
 
</script>

<div class="homebar">
  <a href="/homePage" >
    <img src="/img/home-icon.png" alt="Home" class="home-icon">
  </a>
</div>

<div class="top-bar">
  <a href="/profile">
    <img src="/img/profile-icon.png" alt="Profile" class="profile-icon" />
  </a>
</div>

<style>
  :global(*) {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
  }

  :global(html), :global(body) {
      width: 100%;
      overflow-x: hidden;
      background: rgb(102, 137, 138);
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

  .home-icon {
    width: 25px;
    height: 25px;
    object-fit: cover;
    cursor: pointer;
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

</style>


