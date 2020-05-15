<template>
  <div class="section-container">
    <el-table ref="section-table" :data="tableData" row-key="id" border highlight-current-row>
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
    </el-table>
  </div>
</template>

<script>
import Sortable from 'sortablejs'

export default {
  data() {
    return {
      sortable: null,
      tableData: [
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
    }
  },
  created() {
    this.setSort()
  },
  methods: {
    setSort() {
      const el = this.$refs['section-table'].$el.querySelectorAll(
        '.el-table__body-wrapper > table > tbody'
      )[0]
      this.sortable = Sortable.create(el, {
        ghostClass: 'sortable-ghost', // Class name for the drop placeholder,
        setData: function(dataTransfer) {
          // to avoid Firefox bug
          // Detail see : https://github.com/RubaXa/Sortable/issues/1012
          dataTransfer.setData('Text', '')
        },
        onEnd: evt => {
          const targetRow = this.list.splice(evt.oldIndex, 1)[0]
          this.list.splice(evt.newIndex, 0, targetRow)

          // for show the changes, you can delete in you code
          const tempIndex = this.newList.splice(evt.oldIndex, 1)[0]
          this.newList.splice(evt.newIndex, 0, tempIndex)
        }
      })
    }
  }
}
</script>

<style>
.sortable-ghost {
  opacity: 0.8;
  color: #fff !important;
  background: #42b983 !important;
}
</style>

<style lang="scss" scoped>
.section-container {
  margin: 15px;
}
</style>
