<template>
  <div class="container">
    <div class="header">
      <el-row type="flex" :gutter="20">
        <el-col :span="4">
          <nuxt-link to="/">
            <img src="../../assets/image/logo.jpg" alt class="logo" />
          </nuxt-link>
        </el-col>
        <el-col :span="16">
          <el-row class="middle">
            <el-col :span="3">
              <nuxt-link to="/">首页</nuxt-link>
            </el-col>
            <el-col :span="3">
              <nuxt-link to="/travelStrategy">旅游攻略</nuxt-link>
            </el-col>
            <el-col :span="3">
              <nuxt-link to="/hotel">酒店</nuxt-link>
            </el-col>
            <el-col :span="3">
              <nuxt-link to="/planeTicket">国内机票</nuxt-link>
            </el-col>
            <el-col :span="12"></el-col>
          </el-row>
        </el-col>
        <el-col :span="4">
          <nuxt-link to="/loginAndregister">
            <div>登录/注册</div>
          </nuxt-link>
        </el-col>
      </el-row>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {};
  }
};
</script>

<style lang="less" scoped>
.container {
    border-bottom:1px solid grey;
    box-shadow: 0 3px 0 #f5f5f5;
  .header {
    margin: 0 auto;
    width: 1000px;
    height: 60px;
    line-height: 60px;
    .logo {
      display: block;
      width: 156px;
      height: 42px;
      margin-top: 9px;
    }
    .middle {
      text-align: center;
      div {
        box-sizing: border-box;
        height: 60px;
        a {
          display: block;
        }
        &:hover {
          border-bottom: 5px solid rgb(64, 158, 255);
          color: rgb(64, 158, 255);
        }
        &:last-child {
          border-bottom: 0;
        }
      }
      /deep/ .nuxt-link-exact-active {
        background: #409eff;
        color: #fff !important;
      }
    }
  }
}
</style>


