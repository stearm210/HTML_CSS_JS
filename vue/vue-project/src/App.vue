<template>
  <!-- <template> 标签是Vue组件的模板部分，用于定义组件的HTML结构。 -->
  <div>
    <!-- <h1>{{message}}</h1> -->
    <!-- <element-view> </element-view> -->

    <!-- 员工管理组件 -->
    <emp-view></emp-view>
  </div>
</template>

<!-- <script> 标签是组件的JavaScript部分，定义了组件的行为和数据。 -->
<script>
// EmpView 组件是一个自定义的Vue组件，用于显示员工管理相关的视图。它被导入并注册到当前组件中，所以可以在模板中使用<emp-view>标签来引用它。
import EmpView from "./views/tlias/EmpView.vue";
// import ElementView from "./views/element/ElementView.vue";
export default {
  // components为一个对象，用于注册组件，使得模板中的自定义标签可以使用这些组件
  components: { EmpView /*ElementView */ },
  // data 函数为返回一个对象，这个对象包含了组件的响应式数据。在这个例子中，它返回一个包含message属性的对象。
  data() {
    return {
      message: "Hello vue222",
    };
  },
  // methods 对象。这个对象用于定义组件的方法，但在这个例子中它是空的。
  methods: {},
};
</script>

<!-- <style> 标签。这是组件的样式部分，用于定义组件的CSS。 -->
<style>
</style>


