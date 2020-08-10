<template>
  <div class="home">
    <router-link to="/demo">
      <img class="home__img" src="../assets/play1.svg" alt="play icon">
    </router-link>
  </div>
</template>

<script>

export default {
  name: 'Home',
};

</script>

<style lang="scss">
  .home {
    color: var(--white);
    background-color: var(--darkSlate);
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    height: 100%;

    &__img {
      width: 20rem;
      height: 20rem;
      transition: transform .4s;

      &:hover {
        transform: scale(1.2);
      }
    }
  }
</style>
