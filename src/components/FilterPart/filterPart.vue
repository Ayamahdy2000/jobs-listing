<template>
  <div class="filter-card" id="filter-card">
    <div class="filter-card__bg" v-if="filterList.length > 0">
      <div class="filter-card__items">
        <div v-for="(item, index) in filterList" :key="index">
          <div v-if="item" class="filter-card__item__flex">
            <div class="filter-card__item">
              {{ item }}
            </div>
            <div class="filter-card__icon" @click="removeItem(index)">
              <img src="@/assets/images/icon-remove.svg" alt="icon-remove" />
            </div>
          </div>
        </div>
      </div>
      <p class="clear" @click="removeArr()">Clear</p>
    </div>
  </div>
</template>
<script>
export default {
  props: ["filterList"],
  emits: ["removeItem", "removeArr"],
  setup(props, context) {
    const removeItem = (item) => {
      context.emit("removeItem", item);
    };
    const removeArr = () => {
      context.emit("removeArr");
    };
    return {
      removeItem,
      removeArr,
    };
  },
};
</script>
