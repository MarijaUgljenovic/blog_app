
<script lang="ts">
  

</script>
<div class="background-image"></div>
<div class="background-overlay"></div>


<div class="homebar">
  <a href="/homePage" >
    <img src="/img/home-icon.png" alt="Home" class="home-icon">
  </a>

  <div class="menu-wrapper">
    <a href="/homePage" id="camping" class="choice">
      Camping
    </a>
  
    <div class="dropdown-menu">
      <div class="options">
        <a href="/option1">Settings</a>
        <a href="/option2">Likes</a>
        <a href="/option3">Log out</a>
      </div>
    </div>
  </div>

  <div class="menu-wrapper">
    <a href="/homePage" id="hiking" class="choice">
      Hiking
    </a> 
    <div class="dropdown-menu">
      <div class="options">
        <a href="/option1">Settings</a>
        <a href="/option2">Likes</a>
        <a href="/option3">Log out</a>
      </div>
    </div>
  </div>

  <div class="menu-wrapper">
    <a href="/homePage" id="viaFerrata" class="choice">
      Via ferrata
    </a>  
    <div class="dropdown-menu">
      <div class="options">
        <a href="/option1">Settings</a>
        <a href="/option2">Likes</a>
        <a href="/option3">Log out</a>
      </div>
    </div>
  </div>

  <div class="menu-wrapper">
    <a href="/homePage" id="backpacking" class="choice">
      Backpacking
    </a>  
    <div class="dropdown-menu">
      <div class="options">
        <a href="/option1">Settings</a>
        <a href="/option2">Likes</a>
        <a href="/option3">Log out</a>
      </div>
    </div>
  </div>
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
    position: relative;
    z-index: 0;
    width: 100%;
    height: 100%;
    overflow-x: hidden;
    
    font-family: sans-serif;
 
  }

  .background-image {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background-image: url('/img/poz1.jpg');
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

  .home-icon {
    width: 25px;
    height: 25px;
    object-fit: cover;
    cursor: pointer;
    margin-right: 10px;
  }

 .choice {
    color: white;
    padding-left: 40px;
    text-decoration: none;
 }

 #camping:hover{
  color: #ffcc00;
  }

  .menu-wrapper {
  position: relative;
  display: inline-block;
}

.dropdown-menu {
  display: none;
  position: absolute;
  top: 100%;
  left: 40px; /* isti kao padding linka */
  background-color: #333;
  padding: 1rem;
  border-radius: 8px;
  z-index: 1002;
  min-width: 150px;
}

.menu-wrapper:hover .dropdown-menu {
  display: block;
}

.dropdown-menu a {
  color: white;
  text-decoration: none;
  display: block;
  padding: 0.5rem 0;
}

.dropdown-menu a:hover {
  color: #ffcc00;
}

#hiking:hover{
  color: #ffcc00
}

#viaFerrata:hover{
  color: #ffcc00;
}

#backpacking:hover{
  color: #ffcc00;
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


