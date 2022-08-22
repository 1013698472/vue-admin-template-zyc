<template>
  <div>
    <el-select v-model="value" placeholder="请选择">
      <el-option
        v-for="item in options"
        :key="item.value"
        :label="item.label"
        :value="item.value">
      </el-option>
    </el-select>
    <el-table
      ref="multipleTable"
      :data="tableData"
      tooltip-effect="dark"
      style="width: 100%"
      :default-sort="{prop: 'date', order: 'descending'}"
      @selection-change="handleSelectionChange"
    >
      <el-table-column
        type="selection"
        width="55"
        sortable
      />
      <el-table-column
        prop="date"
        label="注册时间"
        width="120"
        sortable
      >
        <template slot-scope="scope">{{ scope.row.date }}</template>
      </el-table-column>
      <el-table-column
        prop="username"
        label="用户名"
        width="120"
        sortable
      />
      <el-table-column
        prop="name"
        label="姓名"
        width="120"
        sortable
      />
      <el-table-column
        prop="sex"
        label="性别"
        width="120"
        sortable
      />
      <el-table-column
        prop="phone"
        label="手机号"
        width="120"
        sortable
      />

      <el-table-column
        prop="email"
        label="邮箱"
        width="120"
        sortable
      />
      <el-table-column
        prop="address"
        label="地址"
        sortable
        show-overflow-tooltip
      />
      <el-table-column
        fixed="right"
        label="操作"
        width="100">
        <template slot-scope="scope">
          <el-button @click="handleClick(scope.row)" type="text" size="small">查看</el-button>
          <el-button type="text" size="small">编辑</el-button>
        </template>
      </el-table-column>
    </el-table>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        tableData: [{
          date: '2016-05-02',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄'
        }, {
        date: '2016-05-01',
        name: '王小虎',
          address: '上海市普陀区金沙江路 1519 弄'
        }, {
          date: '2016-05-03',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1516 弄'
        }],
        multipleSelection: [],
        options: [{
          value: '选项1',
          label: '全部'
        }, {
          value: '选项2',
          label: '用户名'
        }, {
          value: '选项3',
          label: '姓名'
        }, {
          value: '选项4',
          label: '手机号'
        }, {
          value: '选项5',
          label: '邮箱'
        }],
        value: ''
      }
    },

    methods: {
      handleClick(row) {
        console.log(row);
      },
      // toggleSelection(rows) {
      //   if (rows) {
      //     rows.forEach(row => {
      //       this.$refs.multipleTable.toggleRowSelection(row)
      //     })
      //   } else {
      //     this.$refs.multipleTable.clearSelection()
      //   }
      // },
      handleSelectionChange(val) {
        this.multipleSelection = val
      }
    }
  }
</script>
