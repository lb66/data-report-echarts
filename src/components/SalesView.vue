<template>
  <div class="sales-view">
    <el-card shadow="hover">
      <div slot="header">
        <div class="menu-wrapper">
          <el-menu
            :default-active="activeIndex"
            class="el-menu"
            mode="horizontal"
            @select="handleSelect"
          >
            <el-menu-item index="1">销售额</el-menu-item>
            <el-menu-item index="2">访问量</el-menu-item>
          </el-menu>
          <div class="menu-right">
            <el-radio-group
              v-model="radio"
              size="small"
              :style="{ marginRight: '20px' }"
            >
              <el-radio-button label="今日"></el-radio-button>
              <el-radio-button label="本周"></el-radio-button>
              <el-radio-button label="本月"></el-radio-button>
              <el-radio-button label="今年"></el-radio-button>
            </el-radio-group>
            <el-date-picker
              v-model="value"
              type="daterange"
              range-separator="至"
              start-placeholder="开始日期"
              end-placeholder="结束日期"
              size="small"
            >
            </el-date-picker>
          </div>
        </div>
      </div>
      <div class="sales-chart-wrapper">
        <v-chart :options="chartOptions" />
        <div class="sales-list">
          <div class="list-title">排行榜</div>
          <div class="list-item" v-for="item in rankData" :key="item.no">
            <div :class="['list-item-no', +item.no <= 3 ? 'top-no' : '']">
              {{ item.no }}
            </div>
            <div class="list-item-name">{{ item.name }}</div>
            <div class="list-item-money">{{ item.money }}</div>
          </div>
        </div>
      </div>
    </el-card>
  </div>
</template>

<script>
export default {
  data() {
    return {
      activeIndex: "1",
      radio: "今年",
      value: "",
      chartOptions:{
        title:{
          text:'年度销售额',
          textStyle:{
            fontSize:12,
            color:'#666'
          }
        },
        grid: { bottom: 50, top: 50, right: 40, left: 40 },
        xAxis: {
          type:'category',
          data:['1月','2月','3月','4月','5月','6月','7月','8月','9月','10月','11月','12月'],
          axisTick:{
            alignWithLabel:true,
            lineStyle:{
              color:'#999'
            }
          },
          axisLine:{
            lineStyle:{
              color:'#999'
            }
          },
          axisLabel:{
            color:'#333'
          },
        },
        yAxis: {
          axisLine:{show:false},
          axisTick:{show:false},
          splitLine:{
            lineStyle:{
              type:'dotted',
              color:'#eee'
            }
          }
        },
        series: {
          type:'bar',
          barWidth:'35%',
          data:[200,250,300,200,250,300,200,250,300,200,250,300]
        },
        color:['#3398DB']
      },
      rankData: [
        { no: 1, name: "肯德基", money: "211335" },
        { no: 2, name: "肯德基", money: "211335" },
        { no: 3, name: "肯德基", money: "211335" },
        { no: 4, name: "肯德基", money: "211335" },
        { no: 5, name: "肯德基", money: "211335" },
        { no: 6, name: "肯德基", money: "211335" },
        { no: 7, name: "肯德基", money: "211335" },
      ],
    };
  },
  methods: {
    handleSelect(key, keyPath) {
      this.activeIndex = key;
      console.log(key);
    },
  },
};
</script>

<style lang="scss" scoped>
.sales-view {
  margin-top: 20px;
  .menu-wrapper {
    display: flex;
    align-items: center;
    justify-content: space-between;
    .el-menu .el-menu-item {
      height: 60px;
      line-height: 60px;
      margin-right: 30px;
    }
    .el-menu.el-menu--horizontal {
      border-bottom: none;
    }
  }
  .sales-chart-wrapper {
    display: flex;
    height: 270px;
    .echarts {
      flex: 0 0 70%;
      width: 70%;
      height: 100%;
    }
    .sales-list {
      flex: 1;
      width: 100%;
      height: 100%;
      overflow: hidden;
      .list-title {
        font-size: 12px;
        color: #666;
        font-weight: 500;
      }
      .list-item {
        font-size: 12px;
        display: flex;
        margin: 18px 0;
        .list-item-money{
          margin-left: auto;
        }
        .list-item-no{
          width: 18px;
          height: 18px;
          display: flex;
          justify-content: center;
          align-items: center;
          &.top-no{
            background: #000;
            border-radius: 50%;
            color: #fff;
            font-weight: 500;
          }

        }
        .list-item-name{
          margin-left: 16px;
        }
      }
    }
  }
}
</style>