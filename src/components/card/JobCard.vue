<template>
  <div class="card">
    <div class="row align-items-center">
      <div class="col-lg-6 col-md-7">
        <div class="row align-items-center">
          <div class="col-lg-2 col-md-3">
            <img
              :src="require(`@/assets/images/${item.logo}`)"
              class="card__img"
              alt="company name"
            />
          </div>
          <div class="col-lg-10 col-md-9">
            <div class="card__sub-head">
              {{ item.company }}
              <div
                class="card__sub-head__tag card__sub-head__tag--new"
                v-if="item.new"
              >
                new!
              </div>
              <div
                class="card__sub-head__tag card__sub-head__tag--featured"
                v-if="item.featured"
              >
                featured
              </div>
            </div>
            <h3 class="card__head">{{ item.position }}</h3>

            <p class="card__note">
              <span> {{ item.postedAt }} </span>
              <span class="card__note__dot">.</span>
              <span>{{ item.contract }}</span>
              <span class="card__note__dot"> . </span>
              <span> {{ item.location }}</span>
            </p>
          </div>
        </div>
      </div>
      <div class="col-lg-6 col-md-5">
        <div class="card__tags">
          <div class="card__tag" @click="getFilterData(item.role)">
            {{ item.role }}
          </div>
          <div class="card__tag" @click="getFilterData(item.level)">
            {{ item.level }}
          </div>
          <div
            v-for="(language, index) in item.languages"
            :key="index"
            class="card__tag"
          >
            <div @click="getFilterData(language)">{{ language }}</div>
          </div>
          <div
            v-for="(tool, index) in item.tools"
            :key="index"
            class="card__tag"
          >
            <div @click="getFilterData(tool)">{{ tool }}</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: ["item"],
  emits:["filterData"],
  setup(props,  context) {
    let filterData = [];
    const getFilterData = (item) => {
      filterData.push(item);
        context.emit("filterData" , filterData)
    };
    return {
      filterData,
      getFilterData,
    };
  },
};
</script>
