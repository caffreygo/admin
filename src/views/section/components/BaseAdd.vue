<template>
  <div class="addArticle-form">
    <el-form
      ref="articleForm"
      :label-position="labelPosition"
      label-width="80px"
      :model="articleForm"
      style="width:83%;margin:0 45px"
      :rules="rules"
    >
      <el-form-item label="所属栏目">
        <el-popover
          placement="top-start"
          trigger="hover"
          content="点击选择栏目"
          style="height:50px"
        >
          <el-input slot="reference" value="在线演示" :disabled="true" />
        </el-popover>
      </el-form-item>
      <el-form-item label="标题" prop="title">
        <el-input v-model="articleForm.title" />
      </el-form-item>
      <el-form-item label="短标题">
        <el-input v-model="articleForm.subTitle" />
      </el-form-item>
      <el-form-item label="来源">
        <el-input v-model="articleForm.origin" />
      </el-form-item>
      <el-form-item label="作者">
        <el-input v-model="articleForm.author" />
      </el-form-item>
      <el-form-item label="摘要">
        <el-input v-model="articleForm.abstract" />
      </el-form-item>
      <el-form-item label="内容">
        <el-upload
          class="upload-demo"
          action="https://jsonplaceholder.typicode.com/posts/"
          :on-remove="handleRemove"
          :before-remove="beforeRemove"
          multiple
          :limit="3"
          :on-exceed="handleExceed"
          :file-list="fileList"
        >
          <el-button size="small" type="primary">导入word</el-button>
        </el-upload>
      </el-form-item>
      <el-form-item style="width:100%">
        <tinymce />
      </el-form-item>
      <el-form-item>
        <div class="btn-list">
          <el-button
            type="primary"
            @click="submitArticle('articleForm')"
          >保存</el-button>
          <el-button type="info" @click="revert">返回</el-button>
        </div>
      </el-form-item>
    </el-form>
  </div>
</template>
<script>
import Tinymce from '@/components/Tinymce/index'
export default {
  components: {
    Tinymce
  },
  data() {
    var checkTitle = (rule, value, callback) => {
      if (!value) {
        return callback(new Error('标题不能为空'))
      } else {
        callback()
      }
    }
    return {
      labelPosition: 'right',
      articleForm: {
        title: '',
        subtitle: '',
        origin: '',
        author: '',
        abstract: ''
      },
      rules: {
        title: [{ validator: checkTitle, trigger: 'blur' }]
      },
      fileList: []
    }
  },
  methods: {
    handleRemove(file, fileList) {
      console.log(file, fileList)
    },
    handleExceed(files, fileList) {
      this.$message.warning(
        `当前限制选择 3 个文件，本次选择了 ${
          files.length
        } 个文件，共选择了 ${files.length + fileList.length} 个文件`
      )
    },
    beforeRemove(file, fileList) {
      return this.$confirm(`确定移除 ${file.name}？`)
    },
    submitArticle(formName) {
      this.$refs[formName].validate(valid => {
        if (valid) {
          alert('submit!')
        } else {
          console.log('error submit!!')
          return false
        }
      })
    },
    revert() {
      this.$router.push('/section')
    }
  }
}
</script>
<style lang="scss" scoped>
.addArticle-form {
  .btn-list {
    > button {
      margin-right: 20px;
    }
  }
}
</style>
