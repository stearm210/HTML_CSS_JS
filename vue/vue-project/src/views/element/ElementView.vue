<!-- html代码模版部分 -->
<template>
  <div>
    <!-- button按钮 -->
    <el-row>
      <el-button>默认按钮</el-button>
      <el-button type="primary">主要按钮</el-button>
      <el-button type="success">成功按钮</el-button>
      <el-button type="info">信息按钮</el-button>
      <el-button type="warning">警告按钮</el-button>
      <el-button type="danger">危险按钮</el-button>
    </el-row>

    <!-- table表格样例 -->
    <!-- data表示需要进行显示的数据 -->
    <el-table :data="tableData" border style="width: 100%">
      <el-table-column prop="date" label="日期" width="180"> </el-table-column>
      <el-table-column prop="name" label="姓名" width="180"> </el-table-column>
      <el-table-column prop="address" label="地址"> </el-table-column>
    </el-table>

    <!-- 分页组件 -->
    <!-- background	是否为分页按钮添加背景色 -->
    <!-- layout	组件布局，子组件名用逗号分隔 -->
    <!-- layout中，prev表示上一页。pager表示第几页的按钮。next表示下一个的按钮。total表示按钮中最大的页面表示数为100。jumper表示跳转到某个页面按钮 -->
    <!-- size-change	pageSize 改变时会触发 -->
    <!-- current-change	currentPage 改变时会触发 -->
    <el-pagination
      background
      layout="total, sizes, prev, pager, next ,jumper"
      @size-change="handleSizeChange"
      @current-change="handleCurrentChange"
      :total="1000"
    >
    </el-pagination>

    <!-- Dialog对话框组件 -->
    <!-- Table -->
    <!-- 注意，这里我们设置的dialogTableVisible为true，只有为true时才能打开这个表单，所以一般来说，在没有点击时会默认在script中设置为false，当用户点击之后才会设置为true。 -->
    <el-button type="text" @click="dialogTableVisible = true"
      >打开嵌套表格的 Dialog</el-button
    >

    <el-dialog title="收货地址" :visible.sync="dialogTableVisible">
      <el-table :data="gridData">
        <el-table-column
          property="date"
          label="日期"
          width="150"
        ></el-table-column>
        <el-table-column
          property="name"
          label="姓名"
          width="200"
        ></el-table-column>
        <el-table-column property="address" label="地址"></el-table-column>
      </el-table>
    </el-dialog>

    <!-- Dialog对话框组件-Form表单组件 -->
    <el-button type="text" @click="dialogFormVisible = true"
      >打开嵌套Form的 Dialog</el-button
    >
    <el-dialog title="Form表单" :visible.sync="dialogFormVisible">
      <el-form ref="form" :model="form" label-width="80px">
        <el-form-item label="活动名称">
          <el-input v-model="form.name"></el-input>
        </el-form-item>

        <el-form-item label="活动区域">
          <el-select v-model="form.region" placeholder="请选择活动区域">
            <el-option label="区域一" value="shanghai"></el-option>
            <el-option label="区域二" value="beijing"></el-option>
          </el-select>
        </el-form-item>

        <el-form-item label="活动时间">
          <el-col :span="11">
            <el-date-picker
              type="date"
              placeholder="选择日期"
              v-model="form.date1"
              style="width: 100%"
            ></el-date-picker>
          </el-col>
          <el-col class="line" :span="2">-</el-col>
          <el-col :span="11">
            <el-time-picker
              placeholder="选择时间"
              v-model="form.date2"
              style="width: 100%"
            ></el-time-picker>
          </el-col>
        </el-form-item>

        <el-form-item>
          <el-button type="primary" @click="onSubmit">提交</el-button>
          <el-button>取消</el-button>
        </el-form-item>
      </el-form>
    </el-dialog>
  </div>
</template>

<!-- 定义数组模型和方法 -->
<script>
export default {
  // data用于定义数据模型
  // return主要是用于返回这个组件的效果
  data() {
    return {
      form: {
        name: "",
        region: "",
        date1: "",
        date2: "",
      },
      gridData: [
        {
          date: "2016-05-02",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1518 弄",
        },
        {
          date: "2016-05-04",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1518 弄",
        },
        {
          date: "2016-05-01",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1518 弄",
        },
        {
          date: "2016-05-03",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1518 弄",
        },
      ],
      //   只有当点击之后，dialogTableVisible才会变成true，否则只会显示false。
      dialogTableVisible: false,
      dialogFormVisible: false,
      tableData: [
        {
          date: "2016-05-02",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1518 弄",
        },
        {
          date: "2016-05-04",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1517 弄",
        },
        {
          date: "2016-05-01",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1519 弄",
        },
        {
          date: "2016-05-03",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1516 弄",
        },
      ],
    };
  },
  //   methods用于定义方法
  methods: {
    handleSizeChange: function (val) {
      alert("每页记录数变化" + val);
    },
    handleCurrentChange: function (val) {
      alert("页码发生变化" + val);
    },
    onSubmit() {
      // 输出表单中输入的对象
      alert(JSON.stringify(this.form));
    },
  },
};
</script>

<!-- 定义css代码 -->
<style></style>