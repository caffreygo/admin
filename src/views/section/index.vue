<template>
  <div class="section-container">
    <el-table
      :data="tableData"
      row-key="id"
      border
      highlight-current-row
      @selection-change="handleSelectionChange"
    >
      >
      >
      <el-table-column type="selection" width="55" />
      <el-table-column prop="sectionName" label="栏目名称" sortable width="180" />
      <el-table-column prop="pageIdentification" label="页面标识" sortable width="180" />
      <el-table-column label="有效">
        <template slot-scope="scope">
          <el-tag v-if="scope.row.isEffective">是</el-tag>
          <el-tag v-else type="warning">否</el-tag>
        </template>
      </el-table-column>
      <el-table-column label="导航">
        <template slot-scope="scope">
          <el-tag v-if="scope.row.isNavigation">是</el-tag>
          <el-tag v-else type="warning">否</el-tag>
        </template>
      </el-table-column>
      <el-table-column prop="image" label="栏目图片" />
      <el-table-column prop="sectionTemplate" label="栏目模板" />
      <el-table-column prop="informationTemplate" label="信息模板" />
      <el-table-column align="center" label="排序" width="80">
        <template slot-scope="scope">
          <i class="el-icon-top" @click="handleSort(scope.row,true)" />
          <i class="el-icon-bottom" @click="handleSort(scope.row, false)" />
        </template>
      </el-table-column>
    </el-table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      tableData: []
    }
  },
  created() {
    this.tableData = [
      {
        id: 1,
        index: 1,
        sectionName: '移动APP',
        pageIdentification: '	app',
        isEffective: true,
        isNavigation: true,
        image: '',
        sectionTemplate: 'test.html',
        informationTemplate: 'test.html'
      },
      {
        id: 2,
        index: 2,
        sectionName: '在线演示',
        pageIdentification: '	onlinedemo',
        isEffective: false,
        isNavigation: true,
        image: '',
        sectionTemplate: 'test.html',
        informationTemplate: 'test.html'
      },
      {
        id: 3,
        index: 3,
        sectionName: '帮助中心',
        pageIdentification: 'help',
        isEffective: true,
        isNavigation: false,
        image: '',
        sectionTemplate: 'test.html',
        informationTemplate: 'test.html',
        children: [
          {
            id: 31,
            index: 31,
            sectionName: '操作手册',
            pageIdentification: 'doc',
            isEffective: true,
            isNavigation: true,
            image: '',
            sectionTemplate: 'test.html',
            informationTemplate: 'test.html'
          },
          {
            id: 32,
            index: 32,
            sectionName: '数据对象',
            pageIdentification: 'model',
            isEffective: false,
            isNavigation: true,
            image: '',
            sectionTemplate: 'test.html',
            informationTemplate: 'test.html'
          },
          {
            id: 33,
            index: 33,
            sectionName: '标签库',
            pageIdentification: 'demo',
            isEffective: true,
            isNavigation: true,
            image: '',
            sectionTemplate: 'test.html',
            informationTemplate: 'test.html',
            children: [
              {
                id: 331,
                index: 331,
                sectionName: '操作手册',
                pageIdentification: 'doc',
                isEffective: true,
                isNavigation: true,
                image: '',
                sectionTemplate: 'test.html',
                informationTemplate: 'test.html'
              },
              {
                id: 332,
                index: 332,
                sectionName: '数据对象',
                pageIdentification: 'model',
                isEffective: true,
                isNavigation: true,
                image: '',
                sectionTemplate: 'test.html',
                informationTemplate: 'test.html'
              },
              {
                id: 333,
                index: 333,
                sectionName: '标签库',
                pageIdentification: 'demo',
                isEffective: true,
                isNavigation: true,
                image: '',
                sectionTemplate: 'test.html',
                informationTemplate: 'test.html'
              }
            ]
          }
        ]
      },
      {
        id: 4,
        index: 4,
        sectionName: '移动APP',
        pageIdentification: '	app',
        isEffective: true,
        isNavigation: true,
        image: '',
        sectionTemplate: 'test.html',
        informationTemplate: 'test.html'
      }
    ]
  },
  methods: {
    handleSelectionChange(val) {
      console.log(val)
    },
    handleSort(row, isUp) {
      const index = row.index
      if (isUp) {
        if (index === 1) return
        console.log('up')
      } else {
        if (index === this.tableData.length) return
        console.log('down')
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.section-container {
  margin: 15px 60px 15px 15px;
  @media screen and (max-width: 768px) {
    margin: 15px;
  }
}
</style>
