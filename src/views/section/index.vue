<template>
  <div>
    <div class="section-container">
      <el-table :data="tableData" row-key="id" border highlight-current-row>
        >
        <el-table-column
          prop="sectionName"
          label="栏目名称"
          sortable
          width="180"
        />
        <el-table-column
          prop="pageIdentification"
          label="页面标识"
          sortable
          width="180"
        />
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
            <i class="el-icon-top" @click="handleSort(scope.row, true)" />
            <i class="el-icon-bottom" @click="handleSort(scope.row, false)" />
          </template>
        </el-table-column>
        <el-table-column align="center" label="Drag" width="80">
          <template slot-scope="{}">hello</template>
        </el-table-column>
      </el-table>
    </div>
    <div class="btn-list">
      <el-row>
        <el-button
          v-for="btnItem in btnList"
          :key="btnItem.btnName"
          :type="btnItem.type"
          data-btn="btnItem.btnName"
          @click="handleClick(btnItem.btnName, $event)"
        >{{ btnItem.btnName }}</el-button>
      </el-row>

      <el-dialog
        title="复制到栏目"
        :visible.sync="copyOrRemoveVisible"
        width="35%"
      >
        <el-table
          :data="tableData"
          row-key="id"
          border
          highlight-current-row
          style="width: 100%; margin-bottom: 20px;"
        >
          >
          <el-table-column prop="sectionName" label="栏目名称">
            <template slot-scope="scope">
              <i class="el-icon-folder" />
              <span style="margin-left: 10px;">{{
                scope.row.sectionName
              }}</span>
            </template>
          </el-table-column>
        </el-table>
        <span slot="footer" class="dialog-footer">
          <el-button @click="copyOrRemoveVisible = false">取 消</el-button>
        </span>
      </el-dialog>

      <el-dialog title="提示" :visible.sync="deleteDialogVisible" width="30%">
        <span>确定删除操作么?此操作无法回退!</span>
        <span slot="footer" class="dialog-footer">
          <el-button @click="deleteDialogVisible = false">取 消</el-button>
          <el-button type="primary" @click="handleDelete">确 定</el-button>
        </span>
      </el-dialog>
    </div>

    <div>
      <fluid />
    </div>
  </div>
</template>

<script>
import fluid from './components/index'
export default {
  components: {
    fluid
  },
  data() {
    return {
      tableData: [],
      btnList: [
        {
          btnName: '添加',
          type: 'primary'
        },
        {
          btnName: '编辑',
          type: 'primary'
        },
        {
          btnName: '复制',
          type: 'primary'
        },
        {
          btnName: '移动',
          type: 'primary'
        },
        {
          btnName: '删除',
          type: 'danger'
        },
        {
          btnName: '撤回',
          type: 'primary'
        },
        {
          btnName: '静态化',
          type: 'primary'
        }
      ],
      copyOrRemoveVisible: false,
      deleteDialogVisible: false
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
    },
    handleClick(btnName) {
      if (btnName === '复制' || btnName === '移动') {
        this.copyOrRemoveVisible = true
      } else if (btnName === '删除' || btnName === '撤回') {
        this.deleteDialogVisible = true
      }
    },
    handleDelete() {
      this.$confirm('确定删除?')
        .then((_) => {
          console.log('delete success')
        })
        .catch((_) => {
          console.log('cancel delete')
        })
      this.deleteDialogVisible = false
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
.btn-list {
  margin-left: 15px;
}
</style>
