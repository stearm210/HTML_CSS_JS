<template>
  <div>
    <el-container style="height: 700px; border: 1px solid #eee">
      <!-- 顶部边框 -->
      <el-header style="font-size: 40px; background-color: rgb(238, 241, 246)"
        >智能学习
      </el-header>
      <el-container>
        <!-- 左边框 -->
        <el-aside width="200px">
          <el-menu :default-openeds="['1', '3']">
            <el-submenu index="1">
              <template slot="title"
                ><i class="el-icon-message"></i>系统信息管理</template
              >
              <el-menu-item index="1-1">部门管理</el-menu-item>
              <el-menu-item index="1-2">员工管理</el-menu-item>
            </el-submenu>
          </el-menu>
        </el-aside>

        <!-- 主要展示区域 -->
        <el-main>
          <!-- 表单 -->
          <el-form :inline="true" :model="searchForm" class="demo-form-inline">
            <el-form-item label="姓名">
              <el-input v-model="searchForm.name" placeholder="姓名"></el-input>
            </el-form-item>
            <el-form-item label="性别">
              <el-select v-model="searchForm.gender" placeholder="性别">
                <!-- value中是传递给服务端的数据 -->
                <el-option label="男" value="1"></el-option>
                <el-option label="女" value="2"></el-option>
              </el-select>
            </el-form-item>

            <el-form-item label="入职日期">
              <!-- 日期选择器 -->
              <el-date-picker
                v-model="searchForm.entrydate"
                type="daterange"
                range-separator="至"
                start-placeholder="开始日期"
                end-placeholder="结束日期"
              >
              </el-date-picker>
            </el-form-item>

            <el-form-item>
              <el-button type="primary" @click="onSubmit">查询</el-button>
            </el-form-item>
          </el-form>

          <!-- 表格 -->
          <!-- border加上边框 -->
          <el-table :data="tableDate" border>
            <el-table-column
              prop="name"
              label="姓名"
              width="180"
            ></el-table-column>
            <el-table-column
              prop="image"
              label="图像"
              width="180"
            ></el-table-column>
            <el-table-column
              prop="gender"
              label="性别"
              width="140"
            ></el-table-column>
            <el-table-column
              prop="job"
              label="职位"
              width="140"
            ></el-table-column>
            <el-table-column
              prop="entrydate"
              label="入职日期"
              width="180"
            ></el-table-column>
            <el-table-column
              prop="updatetime"
              label="最后操作时间"
              width="230"
            ></el-table-column>
            <el-table-column label="操作">
              <el-button type="primary" size="mini">编辑</el-button>
              <el-button type="danger" size="mini">删除</el-button>
            </el-table-column>
          </el-table>

          <!-- 增加分页条 -->
          <el-pagination
            background
            layout="total, sizes, prev, pager, next ,jumper"
            @size-change="handleSizeChange"
            @current-change="handleCurrentChange"
            :total="1000"
          >
          </el-pagination>
        </el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      tableDate: [],
      searchForm: {
        name: "",
        gender: "",
        entrydate: [],
      },
    };
  },
  methods: {
    onSubmit: function () {
      alert("查询数据");
    },
    handleSizeChange: function (val) {
      alert("每页记录数变化" + val);
    },
    handleCurrentChange: function (val) {
      alert("页码发生变化" + val);
    },
  },
  mounted() {
    //钩子函数
    axios
      .get("http://yapi.smart-xwork.cn/mock/169327/emp/list")
      .then((result) => {
        this.tableDate = result.data.data; //返回对应的数组
      });
  },
};
</script>

<style></style>
