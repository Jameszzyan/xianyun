<template>
  <div class="flights">
    <section class="contianer">
      <el-row type="flex" justify="space-between">
        <!-- 顶部过滤列表 -->
        <div class="flights-content">
          <!-- 过滤条件 -->
          <div></div>

          <!-- 航班头部布局 -->
          <div>
            <flights-header></flights-header>
            <flights-item :list="item" v-for="(item,index) in showList" :key="index + '.' +item.airline_name + '~' +item.dep_datetime +item.arr_datetime + item.flight_no + Math.random()"></flights-item>
            <el-pagination
              @size-change="handleSizeChange"
              @current-change="handleCurrentChange"
              :current-page="currentPage"
              :page-sizes="[10, 20, 30, 40]"
              :page-size="pageSize"
              layout="total, sizes, prev, pager, next, jumper"
              :total="total"
            ></el-pagination>
          </div>

          <!-- 航班信息 -->
          <div></div>
        </div>

        <!-- 侧边栏 -->
        <div class="aside">
          <!-- 侧边栏组件 -->
        </div>
      </el-row>
    </section>
  </div>
</template>

<script>



export default {
  data() {
    return {
        dataList:[],
        showList:[],
        pageSize:10,
        currentPage:1,
        total:50
    };
  },
  methods: {
    init() {
      this.$axios({
        url: "airs",
        method: "get",
        params: this.$route.query
      })
        .then(result => {
          this.dataList = result.data.flights
          this.total = this.dataList.length
          this.handlePagination()
        })
        .catch(err => {
          console.log(err);
        });
    },

    handlePagination(){
        this.showList = this.dataList.slice((this.currentPage-1)*this.pageSize,this.currentPage*this.pageSize)
    },
    handleSizeChange(val){
        this.pageSize = val
        this.handlePagination()
    },
    handleCurrentChange(val){
        this.currentPage = val
        this.handlePagination()
    }
  },
  mounted() {
    this.init();
  },
  components: {
    flightsHeader: () => import("@/components/planeTicket/flightsHeader"),
    flightsItem: () => import("@/components/planeTicket/flightsItem")
  }
};
</script>

<style lang="less" scoped>
.contianer {
  width: 1000px;
  margin: 20px auto;
}

.flights-content {
  width: 745px;
  font-size: 14px;
}

.aside {
  width: 240px;
}
</style>


