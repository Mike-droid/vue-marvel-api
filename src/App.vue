<template>
  <header class="header">
    <h1 class="title">Some random Marvel heroes with </h1>
    <img src="@/assets/logo.png" alt="Vue JS 3">
  </header>
  <router-view/>
</template>

<style lang="scss">
body {
  background: rgb(251,112,19);
  background: radial-gradient(circle, rgba(251,112,19,1) 0%, rgba(160,41,1,1) 29%, rgba(118,26,3,1) 49%, rgba(216,55,55,1) 100%);
  font-family: 'Marvel', sans-serif;
}

body::-webkit-scrollbar{
    width: 1em;
}

body::-webkit-scrollbar-track{
    background: #df831a;
}

body::-webkit-scrollbar-thumb{
    background: white;
}

.header {
  color: white;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;

  & img {
    height: 50px;
    width: 50px;
  }
}
</style>
