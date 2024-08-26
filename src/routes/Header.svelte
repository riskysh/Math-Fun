<script>
	
</script>

<nav class="navbar">
    <div class="logo">Untitled</div>

    <ul class="nav-links">

      <input type="checkbox" id="checkbox_toggle" />
      <label for="checkbox_toggle" class="hamburger">&#9776;</label>

      <div class="menu">

        <li><a href="/">Illustrations</a></li>
        <li><a href="/">Artists</a></li>
      </div>
    </ul>
  </nav>

<style>

@import url('https://fonts.googleapis.com/css2?family=Lexend:wght@100..900&display=swap');

.navbar {
  font-family: 'Lexend', sans-serif;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

a {
  text-decoration: none;
}

li {
  list-style: none;
}

.navbar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 20px;
  color: #fff;
}

.nav-links a {
  color: #fff;
}

.logo {
  font-size: 32px;
  cursor: pointer;
}

.menu {
  display: flex;
  gap: 1em;
  font-size: 18px;
}

.menu a:hover {
  color: #57F287;
  transition: 0.3s ease;
}

.menu li {
  padding: 5px 14px;
}

input[type=checkbox] {
  display: none;
} 

/* HAMBURGER MENU */
.hamburger {
  display: none;
  font-size: 24px;
  user-select: none;
  cursor: pointer;
}

/* APPLYING MEDIA QUERIES */
@media (max-width: 768px) {
 .menu {
    display:none;
    position: absolute;
    right: 0;
    left: 0;
    text-align: center;
    padding: 16px 0;
  }

  .menu a:hover {
    display: inline-block;
    color:#57F287;
    transition: 0.3s ease;
  }

  .menu li + li {
    margin-top: 12px;
  }

  input[type=checkbox]:checked ~ .menu {
    display: block;
  }

  .hamburger {
    display: block;
  }
}
</style>
