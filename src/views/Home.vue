<template>
  <h1>Home</h1>

  <nav class="navigation">
    <router-link
      to="/quiz"
      class="navigation_link"
      exact-active-class="navigation__link--exact-active"
      >クイズ</router-link
    >
    <router-link
      to="/palette"
      class="navigation_link"
      exact-active-class="navigation__link--exact-active"
      >パレット</router-link
    >
    <router-link
      to="/memo"
      class="navigation_link"
      exact-active-class="navigation__link--exact-active"
      >メモ</router-link
    >
  </nav>
</template>

<style>
.navigation {
  display: flex;
  justify-content: center;
  align-items: flex-end;
}

.navigation_link {
  display: flex;
  justify-content: space-between;
  align-items: center;
  position: relative;
  margin: 2rem;
  padding: 1rem;
  width: 200px;
  color: rgb(51, 51, 51);
  font-size: 18px;
  font-weight: 700;
  background-color: #3dc085a1;
  transition: 0.3s;
  border-radius: 30px;
}

.navigation_link::before {
  /*枠線部分 */
  content: "";
  position: absolute;
  top: -5px;
  left: -5px;
  width: calc(100% - 4px);
  height: calc(100% - 4px);
  border: 2px solid #42b983;
  transition: 0.2s;
  border-radius: 30px;
}

.navigation_link::after {
  /* 矢印のところ */
  content: "";
  width: 5px;
  height: 5px;
  border-top: 3px solid #333333;
  border-right: 3px solid #333333;
  transform: rotate(45deg);
}

.navigation_link:hover::before {
  top: 0;
  left: 0;
}

.navigation_link:hover {
  text-decoration: none;
  background-color: #34be80;
}
</style>

<script></script>
