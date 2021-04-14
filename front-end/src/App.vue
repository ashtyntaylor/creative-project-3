<template>
<div id="app">
  <div class="header">
    <router-link to="/">
      <img class="logo" src="/images/movielogo.png">
    </router-link>
    <div class="title">
      <h1>Movie Recommender</h1>
    </div>
    <router-link to="/library">
      <img class="manageLibrary" src="/images/manageLibrary.png">
    </router-link>
    <router-link to="/browse">
      <img class="navigation" src="/images/browseMovies.png">
    </router-link>
  </div>
  <div class="content">
    <router-view />
  </div>
  <div class="footer">
    <div class="footer-item">
      <a href="https://github.com/ashtyntaylor/creative-project-3">Github Repository</a>
    </div>
  </div>
</div>
</template>

<style>
html {
  box-sizing: border-box;
}

body {
  font-family: 'Montserrat', sans-serif;
  font-size: 16px;
  background: #fff;
  padding: 0px;
  margin: 0px;
}

/* Header */
.header {
  display: flex;
  padding: 0px 100px 0px 100px;
  background-color: #cce6ff;
  color: #1C454F;
}

.title {
  margin-top: 5px;
}

.title h1 {
  font-size: 30px;
}

.content {
  padding: 20px 100px;
  min-height: 500px;
}

/* Footer */
.footer a {
  color: black;
  text-decoration: none;
}

.footer a:hover {
  color: #e74c3c;
}

.footer-item {
  text-align: center;
  flex: 1;
  padding-top: 30px;
}

h1 {
  font-size: 20px;
  padding-top: 7px;
}

h2 {
  font-size: 14px;
}

h3 {
  font-size: 12px;
}

.logo {
  height: 100px;
  padding-right: 30px;
  padding-bottom: 10px;
}

.navigation {
  height: 20px;
  padding-top: 40px;
  padding-right: 15px;
  position: absolute;
  right: 0%;
}
.manageLibrary {
  height: 20px;
  padding-top: 40px;
  position: absolute;
  right: 12%;
}

/* menu on medium-sized screens */
@media only screen and (max-width: 1150px) and (min-width: 648px) {
  .navigation{
    padding-top: 60px;
    padding-right: 10px;
  }

  .manageLibrary {
    padding-top: 20px;
    padding-right: 10px;
    right: 0%;
  }
}

/* menu on small screens */
@media only screen and (max-width: 647px) and (min-width: 500px) {
  .navigation {
    padding-top: 105px;
    height: 20px;
  }

  .manageLibrary {
    padding-top: 105px;
    right: 25%;
    height: 20px;
  }

  .header {
    padding-bottom: 20px;
  }
}

</style>
