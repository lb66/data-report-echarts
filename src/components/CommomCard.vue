<template>
  <div class="commom-card">
    <div class="title">{{ title }}</div>
    <div class="value">{{ value }}</div>
    <div class="chart">
      <slot />
    </div>
    <div class="line"></div>
    <div class="total">
      <slot name="footer" />
    </div>
  </div>
</template>

<script>
export default {
  props: {
    title: String,
    value: String,
  },
};
</script>

<style lang="scss" scoped>
.title {
  font-size: 12px;
  color: #999;
}
.value {
  font-size: 24px;
  color: #000;
  margin-top: 6px;
  letter-spacing: 1px;
}
.chart {
  height: 50px;
}
.line {
  margin: 10px 0;
  border-top: 1px solid #e6e6e6;
}
.total {
  font-size: 12px;
  color: #666;
}
</style>

<style >
.emphasis {
  margin-left: 6px;
  color: #333;
  font-weight: 700;
}
</style>