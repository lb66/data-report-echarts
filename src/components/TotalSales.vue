<template>
  <div>
    <commom-card title="累计销售额" value="￥ 32,456,789">
      <template >
        <div class="compare-wrapper">
          <div class="compare">
            <span>日同比</span>
            <span class="emphasis">7.33%</span>
          </div>
          <div class="compare">
            <span>月同比</span>
            <span class="emphasis">7.33%</span>
          </div>
        </div>
      </template>
      <template v-slot:footer>
        <span>昨日销售额</span>
        <span class="emphasis">￥ 30,000</span>
      </template>
    </commom-card>
  </div>
</template>

<script>
import CommomCard from "./CommomCard.vue";

export default {
  components: { CommomCard },
};
</script>

<style lang="scss" scoped>
.compare-wrapper {
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  .compare {
    font-size: 12px;
    margin-top: 3px;
  }
}


</style>