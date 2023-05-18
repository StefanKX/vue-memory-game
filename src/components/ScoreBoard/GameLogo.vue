<template>
  <h1 class="logo">LEGENDÄR - von Schulzeit bis Hochzeit</h1>
</template>

<style scoped>
.logo {
  display: flex;
  height: 50px;
  padding: 10px 10px 10px 10px;
  border-radius: 5px;
  background-color: #5979ac;
  color: #fff;
  text-align: center;
}
a {
  text-decoration: none;
  color: #fff;
}

@media screen and (max-width: 450px) {
  .logo {
    width: 150px;
  }
}

@media screen and (max-width: 380px) {
  .logo {
    width: 140px;
  }
}

@media screen and (max-width: 360px) {
  .logo {
    width: 110px;
  }
  a {
    font-size: 12px;
  }
}
</style>
