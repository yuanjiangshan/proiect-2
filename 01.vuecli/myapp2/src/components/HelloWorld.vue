<template>
  <div class="hello">
    <el-row class="tac">
      <el-col :span="24">
        <el-avatar :size="100" src="https://empty" @error="errorHandler" class="touxiang">
          <img src="https://cube.elemecdn.com/e/fd/0fc7d20532fdaf769a25683617711png.png"/>
        </el-avatar>
        <span class="gangwei">部门介绍</span>
        <el-menu
          default-active="2"
          class="el-menu-vertical-demo"
          @open="handleOpen"
          @close="handleClose">
          <el-submenu v-for="(item,index) in bumen" :key="index" class="one1" :index="item.id">
            <template slot="title">
              <span class="one_bumen">{{item.bumen}}</span>
            </template>
            <el-menu-item-group>
              <el-menu-item v-for="(items,index) in item.gangwei" :key="index" :index="items.gangwei_id">{{items.name}}</el-menu-item>
            </el-menu-item-group>
          </el-submenu>
        </el-menu>
      </el-col>
    </el-row>
    <div class="yuangong">
      <div class="biaoti">
        <h2>员工信息</h2>
      </div>
      <!-- 下面的是id -->
      <el-table
        :data="tableData"
        style="width: 100%">
        <el-table-column
          label="id"
          width="180">
          <template slot-scope="scope">
            <span style="margin-left: 10px">{{ scope.row.id }}</span>
          </template>
        </el-table-column>
      <!-- 下面的是姓名 -->
        <el-table-column
          label="姓名"
          width="180">
          <template slot-scope="scope">
            <el-popover placement="top">
              <p>姓名: {{ scope.row.name }}</p>
              <!-- <p>住址: {{ scope.row.address }}</p> -->
              <div slot="reference" class="name-wrapper">
                <span>{{ scope.row.name }}</span>
              </div>
            </el-popover>
          </template>
        </el-table-column>
        <!-- 下面的是性别 -->
        <el-table-column
          label="性别"
          width="180">
          <template slot-scope="scope">
            <span style="margin-left: 10px">{{ scope.row.gender }}</span>
          </template>
        </el-table-column>
        <!-- 下面的是日期 -->
        <el-table-column
          label="出身日期"
          width="180">
          <template slot-scope="scope">
            <i class="el-icon-time"></i>
            <span style="margin-left: 10px">{{ scope.row.date }}</span>
          </template>
        </el-table-column>
        <!-- 下头的是备注 -->
        <el-table-column
          label="备注"
          width="180"
          class="yuangong_jz">
          <template slot-scope="scope">
            <span style="margin-left: 10px">{{ scope.row.remarks }}</span>
          </template>
        </el-table-column>

        <el-table-column label="操作" width="360">
          <template slot-scope="scope">
            <el-button
              size="mini"
              @click="handleEdit(scope.$index, scope.row)">编辑</el-button>
            <el-button
              size="mini"
              @click="handleSave(scope.$index, scope.row)">保存</el-button>
            <el-button
              size="mini"
              type="danger"
              @click="handleDelete(scope.$index, scope.row)">删除</el-button>
          </template>
        </el-table-column>
      </el-table>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      tableData: [{
        id: '2016042294',
        date: '2016-05-02',
        gender: '男',
        remarks: '',
        name: '王大拿'
      }, {
        id: '2016042295',
        date: '2016-05-04',
        gender: '女',
        name: '刘小娜',
        remarks: ''
      }, {
        id: '2016042296',
        date: '2016-05-01',
        name: '胖虎',
        remarks: '',
        gender: '男'
      }, {
        id: '2016042297',
        gender: '女',
        date: '2016-05-03',
        remarks: '',
        name: '亚斯娜'
      }],
      bumen: [
        {
          id: 1,
          bumen: '技术部门',
          gangwei: [
            {
              gangwei_id: 11,
              name: '嵌入式软件开发'
            },
            {
              gangwei_id: 21,
              name: 'Android开发'
            },
            {
              gangwei_id: 31,
              name: 'web前端开发'
            }]
        },
        {
          id: 2,
          bumen: '研发部门',
          gangwei: [
            {
              gangwei_id: 41,
              name: '嵌入式软件开发'
            },
            {
              gangwei_id: 51,
              name: 'Android开发'
            },
            {
              gangwei_id: 61,
              name: 'web前端开发'
            }]
        },
        {
          id: 3,
          bumen: '销售部门',
          gangwei: [
            {
              gangwei_id: 71,
              name: '嵌入式软件开发'
            },
            {
              gangwei_id: 81,
              name: 'Android开发'
            },
            {
              gangwei_id: 91,
              name: 'web前端开发'
            }]
        }]
    }
  },
  methods: {
    handleOpen (key, keyPath) {
      console.log(key, keyPath)
    },
    handleClose (key, keyPath) {
      console.log(key, keyPath)
    },
    handleEdit (index, row) {
      console.log(index, row)
    },
    handleDelete (index, row) {
      console.log(index, row)
    },
    handleSave (index, row) {
      console.log(index, row)
    },
    errorHandler () {
      return true
    }
  }
}
</script>

<style>
@import url("./HelloWorld.css");
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
