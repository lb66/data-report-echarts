<template>
  <div class="bottom-view">
    <div class="view" :style="{ marginRight: '10px' }">
      <el-card shadow="hover">
        <div slot="header">
          <div class="title">关键词搜索</div>
        </div>
        <div class="chart-wrapper">
          <div class="chart">
            <div class="chart-title">搜索用户数</div>
            <div class="chart-data">98,456</div>
            <v-chart :options="userOption" />
          </div>
          <div class="chart">
            <div class="chart-title">搜索量</div>
            <div class="chart-data">198,456</div>
            <v-chart :options="userOption" />
          </div>
        </div>
        <div class="table-wrapper">
          <el-table :data="tableData" style="width: 100%">
            <el-table-column prop="rank" label="排名" width="180" />
            <el-table-column prop="keyword" label="关键词" width="180" />
            <el-table-column prop="count" label="姓总搜索量" />
            <el-table-column prop="users" label="搜索用户数" />
            <el-table-column prop="range" label="点击率" />
          </el-table>
          <el-pagination
            layout="prev, pager, next"
            :total="100"
            background
            :page-size="4"
            @current-change="onChangePage"
          />
        </div>
      </el-card>
    </div>
    <div class="view" :style="{ marginLeft: '10px' }">
      <el-card shadow="hover">
        <div slot="header">
          <div class="title-wrapper">
            <div class="title">分类销售排行</div>
            <div class="radio-wrapper">
              <el-radio-group v-model="radio" size="small">
                <el-radio-button label="品类">品类</el-radio-button>
                <el-radio-button label="商品">商品</el-radio-button>
              </el-radio-group>
            </div>
          </div>
        </div>
        <template>
          <v-chart :options="categoryOption" />
        </template>
      </el-card>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      userOption: {
        xAxis: {
          type: "category",
          boundaryGap: false,
        },
        yAxis: { show: false },
        series: [
          {
            type: "line",
            data: [250, 100, 150, 200, 100, 150, 200, 100, 150, 200],
            areaStyle: {
              color: "#c7e7ff",
            },
            lineStyle: {
              color: "#5fbbff",
            },
            itemStyle: {
              opacity: 0,
            },
            smooth: true,
          },
        ],
        grid: { bottom: 0, top: 0, right: 0, left: 0 },
      },
      numberOption: {},
      radio: "品类",
      categoryOption: {},
      tableData: [
        {
          id: 1,
          rank: 1,
          keyword: "杭州",
          count: 100,
          users: 90,
          range: "90%",
        },
        {
          id: 1,
          rank: 1,
          keyword: "杭州",
          count: 100,
          users: 90,
          range: "90%",
        },
        {
          id: 1,
          rank: 1,
          keyword: "杭州",
          count: 100,
          users: 90,
          range: "90%",
        },
        {
          id: 1,
          rank: 1,
          keyword: "杭州",
          count: 100,
          users: 90,
          range: "90%",
        },
      ],
    };
  },
  methods: {
    onChangePage(e) {
      console.log(e);
    },
  },
};
</script>

<style lang="scss" scoped>
.bottom-view {
  margin-top: 20px;
  display: flex;
  .view {
    flex: 1;
    font-size: 14px;
    .title {
      margin: 20px 0;
    }
    .chart-wrapper {
      display: flex;
      .chart {
        flex: 1;
        padding: 0 20px;
        .chart-title {
          color: #999;
        }
        .chart-data {
          font-size: 22px;
          color: #333;
          font-weight: 500;
          letter-spacing: 2px;
        }
        .echarts {
          height: 50px;
        }
      }
    }
    .table-wrapper {
      flex: 1;
      padding: 20px 20px 0 20px;
      .el-pagination {
        margin-top: 20px;
        display: flex;
        justify-content: flex-end;
      }
    }
    .title-wrapper {
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
  }
}
</style>