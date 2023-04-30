<template>
  <div>
    <header class="header">
      <div class="header__inner">
        <picture>
          <source
            media="(min-width:768px)"
            srcset="@/assets/images/bg-header-desktop.svg"
          />
          <source
            media="(min-width:320px)"
            srcset="@/assets/images/bg-header-mobile.svg"
          />
          <img src="@/assets/images/bg-header-desktop.svg" alt="bg-header" />
        </picture>
      </div>
    </header>
    <main class="main container">
      <job-card></job-card>
      <job-card></job-card>
    </main>
  </div>
</template>

<script>
import JobCard from "./components/card/JobCard.vue";
export default {
  name: "App",
  components: {
    JobCard,
  },
};
</script>
<!-- Main style -->
<style lang="scss">
@import "assets/styles/main.scss";
</style>
