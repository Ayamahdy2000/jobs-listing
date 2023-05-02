<template>
  <div>
    <header>
      <div class="header">
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
      </div>
      <div class="container">
        <div class="filter" id="filter">
          <filter-part
            :filterList="filterList"
            @removeItem="removeItem"
            @removeArr="removeArr"
          />
        </div>
      </div>
    </header>
    <main class="main container">
      <div v-for="(item, index) in jobs" :key="index">
        <job-card
          :item="item"
          @filterData="filterData"
          :filterList="filterList"
        ></job-card>
      </div>
    </main>
  </div>
</template>

<script>
import JobCard from "./components/card/JobCard.vue";
import jobsListing from "./assets/data.json";
import FilterPart from "./components/FilterPart/filterPart.vue";
import { ref } from "vue";
export default {
  name: "App",
  components: {
    JobCard,
    FilterPart,
  },
  setup() {
    let jobs = ref(jobsListing);
    let filterList = ref([]);
    const filterData = (value) => {
      filterList.value = [...filterList.value, value];
      filterList.value = [...new Set(filterList.value)];
      setTimeout(() =>{
        divHeight();
      },0)
    };
    const removeItem = (value) => {
      filterList.value.splice(value, 1);
       setTimeout(() =>{
        divHeight();
      },0)
    };
    const divHeight = () => {
      let filterCard = document.getElementById("filter-card").clientHeight;
      filterCard = filterCard / 2;
      document.getElementById("filter").style.height = filterCard + "px";
    };
    const removeArr = () => {
      filterList.value = [];
       setTimeout(() =>{
        divHeight();
      },0)
    };
    return {
      jobs,
      filterData,
      filterList,
      removeItem,
      removeArr,
      divHeight,
    };
  },
};
</script>
<!-- Main style -->
<style lang="scss">
@import "assets/styles/main.scss";
</style>
