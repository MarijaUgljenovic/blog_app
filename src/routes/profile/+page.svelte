<script lang="ts">

    import { onMount } from 'svelte';

    let showMenu = false;

    function toggleMenu() {
    showMenu = !showMenu;
    }

    function closeMenu() {
    showMenu = false;
    }

    // Definiši akciju
    function clickOutside(node: HTMLElement) {
    const handleClick = (event: MouseEvent) => {
        if (!node.contains(event.target as Node)) {
        closeMenu();
        }
    };

    document.addEventListener('click', handleClick, true);

    return {
        destroy() {
        document.removeEventListener('click', handleClick, true);
        }
    };
}
</script>

<div class="homebar">
    <a href="/homePage" >
      <img src="/img/home-icon.png" alt="Home" class="home-icon">
    </a>
    <img src="/img/search-icon.png" alt="Search" class="search-icon">
</div>

  <div class="top-bar">
    <a href="/profile">
        <img src="/img/profile-icon.png" alt="Profile" class="profile-icon" />
      </a>
  
      <div style="position: relative;">
          <button type="button" on:click={toggleMenu} class="menu-button">
              <img src="/img/menu-icon.png" alt="Menu" class="menu-icon" />
          </button>
        
          {#if showMenu}
            <div class="dropdown-menu" use:clickOutside>
                <div class="image-container">
                    <img src="/img/profile-icon.png" alt="Profile" class="image-prf" />
                  </div>
                  <div class="options">
                    <a href="/option1" on:click={closeMenu}>Settings</a>
                    <a href="/option2" on:click={closeMenu}>Likes</a>
                    <a href="/option3" on:click={closeMenu}>Log out</a>
                  </div>
            </div>
          {/if}
        </div>
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

  .search-icon {
    margin-left: 50px;
    width: 18px;
    height: 18px;
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

  .menu-icon {
    width: 32px;
    height: 32px;
    object-fit: cover;
    cursor: pointer;
  }

  .menu-button {
    background: none;
    border: none;
    padding: 0;
    cursor: pointer;
  }

  .dropdown-menu {
    position: fixed;
    top: 50%; 
    left: 50%;
    transform: translate(-50%, -50%);
    background-color: #1f1e1e;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 2);
    border-radius: 4px;
    padding: 20px;
    overflow: hidden;
    display: flex;
    flex-direction: column;
    z-index: 1002;
    align-items: left;
    width: 300px;
    height: 400px;
    
  }

  .image-prf {
    margin: 10px auto;
    display: block;
    width: 80px;
    height: 80px;
    border-radius: 50%;
    object-fit: cover;
    cursor: pointer;
  }

  .image-container {
    display: flex;
    justify-content: center;
    padding: 10px;
  }

  .image-container :hover{
    background-color: #646060;
  }

  .options{
    margin-top: 30px;
  }

  .dropdown-menu a {
    padding: 10px 20px;
    text-decoration: none;
    color: #fdfdfd;
    display: block;
  }

  .dropdown-menu a:hover {
    text-decoration: underline;
  }


</style>


