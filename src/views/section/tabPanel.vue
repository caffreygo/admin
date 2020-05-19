<template>
  <div class="tab-panel">
    <div class="form-title">
      <i class="el-icon-edit" />
      <span>信息编辑</span>
    </div>
    <div class="tab">
      <template>
        <el-tabs v-model="activeName" type="card">
          <el-tab-pane label="基本">
            <base-add />
          </el-tab-pane>
          <el-tab-pane label="分页内容">
            <!-- <pagination /> -->
          </el-tab-pane>
          <el-tab-pane label="附件">角色管理</el-tab-pane>
          <el-tab-pane label="图片集">定时任务补偿</el-tab-pane>
          <el-tab-pane label="视频">配置管理</el-tab-pane>
          <el-tab-pane label="高级">角色管理</el-tab-pane>
          <el-tab-pane label="自定义">定时任务补偿</el-tab-pane>
        </el-tabs>
      </template>
    </div>
  </div>
</template>
<script>
import BaseAdd from './components/BaseAdd'
// import Pagination from "./components/Pagination";
export default {
  components: {
    BaseAdd
    // Pagination
  },
  data() {
    return {
      activeName: ''
    }
  }
}
</script>
<style lang="scss" scoped>
.tab-panel {
  width: 95%;
  background: none repeat scroll 0 0 #f9f9f9;
  border: 1px solid #cdcdcd;
  margin: 10px auto;
  .form-title {
    height: 36px;
    background-color: #efefef;
    .el-icon-edit {
      height: 100%;
      border-right: 1px solid #cdcdcd;
      padding: 9px 10px 7px 11px;
      float: left;
      opacity: 0.7;
    }
    span {
      color: #666666;
      text-shadow: 0 1px 0 #ffffff;
      float: left;
      font-size: 12px;
      font-weight: bold;
      padding: 12px;
      line-height: 12px;
      margin: 0;
    }
  }
}
</style>
