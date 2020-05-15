<template>
  <div class="addArticle-form">
    <div class="form-title">
      <i class="el-icon-edit" />
      <span>信息编辑</span>
    </div>
    <div class="tab">
      <template>
        <el-tabs v-model="activeName" type="card">
          <el-tab-pane label="基本">
            <el-form
              :label-position="labelPosition"
              label-width="80px"
              :model="formLabelAlign"
              style="width:80%;margin:0 auto"
            >
              <el-form-item label="所属栏目">
                <el-input value="在线演示" disabled="true" />
              </el-form-item>
              <el-form-item label="标题">
                <el-input v-model="formLabelAlign.name" />
              </el-form-item>
              <el-form-item label="短标题">
                <el-input v-model="formLabelAlign.region" />
              </el-form-item>
              <el-form-item label="来源">
                <el-input v-model="formLabelAlign.type" />
              </el-form-item>
              <el-form-item label="作者">
                <el-input v-model="formLabelAlign.name" />
              </el-form-item>
              <el-form-item label="摘要">
                <el-input v-model="formLabelAlign.region" />
              </el-form-item>
              <el-form-item label="内容">
                <el-button type="primary">导入word</el-button>
              </el-form-item>
            </el-form>
          </el-tab-pane>
          <el-tab-pane label="分页内容">配置管理</el-tab-pane>
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
export default {
  data() {
    return {
      activeName: '',
      labelPosition: 'right',
      formLabelAlign: {
        name: '',
        region: '',
        type: ''
      }
    }
  }
}
</script>
<style lang="scss" scoped>
.addArticle-form {
  width: 95%;
  background: none repeat scroll 0 0 #f9f9f9;
  border-top: 1px solid #cdcdcd;
  border-left: 1px solid #cdcdcd;
  border-right: 1px solid #cdcdcd;
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
