<template>
  <div id="app">

    <transition name="slide-fade" mode="out-in">
      <router-view/>
    </transition>

  </div>
</template>

<style lang="scss">

body,
html {
  --darkSlate: #253746;
  --darkerSlate: rgba(0,0,0,.1);
  --electricTeal: #00bcb5;
  --coolGray: #98a4af;
  --black: #000000;
  --hotPink: #e72176;
  --white: #ffffff;
  --lightGray: #e5e5e5;
  --md-theme-default-primary: var(--electricTeal);
  --md-theme-default-primary-on-background: var(--electricTeal);
  height: 100%;
  width: 100%;
  overflow-x:hidden;
  margin: 0;
  padding: 0;
  font-size: 10px;
  line-height: normal;
  color: var(--white);
  background-color: var(--darkSlate);

   * {
    box-sizing: border-box;
  }
}

.mobile-open {
  display: block;
}

a {
  color: inherit;
}

#app {
  font-family: 'museo-sans-rounded', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  font-size: 1.4rem;
  height: 100%;
  color: var(--white);
  background-color: var(--darkSlate);
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: var(--white);

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}

.slide-fade-enter-active {
  transition: all .6s ease;
}

.slide-fade-leave-active {
  transition: all .6s ease;
}

.slide-fade-enter, .slide-fade-leave-to {
  transform: translateX(-20px);
  opacity: 0;
}
</style>
