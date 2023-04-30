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
      <div v-for="(item, index) in jobs" :key="index">
        <job-card :item="item" @filterData="filterData"></job-card>
     
      </div>
    </main>
  </div>
</template>

<script>
import JobCard from "./components/card/JobCard.vue";
import jobsListing from "./assets/data.json";
export default {
  name: "App",
  components: {
    JobCard,
  },
  setup(){
    let jobs  = jobsListing
    let filterList = []
    const filterData  = (value) =>{
      filterList = value
      console.log(filterList)
    }
    return{
      jobs,
      filterData,
      filterList
    }
  },
  
};
</script>
<!-- Main style -->
<style lang="scss">
@import "assets/styles/main.scss";
</style>
