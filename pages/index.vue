<template>
  <el-container style="height: 500px; border: 1px solid #eee">
  <el-aside width="200px" style="background-color: rgb(238, 241, 246)">
    <el-menu :default-openeds="['1']">
      <el-submenu index="1">
        <template slot="title"><i class="el-icon-message"></i>工业经济指标</template>
        <el-submenu index="1-1">
          <template slot="title">东方财富证券</template>
          <el-menu-item index="1-1-1" title="国内生产总值同比增长速度">GDP</el-menu-item>
          <el-menu-item index="1-1-2" title="制造业采购经理指数">PMI</el-menu-item>
           <el-menu-item index="1-1-3" title="工业品出厂价格指数">PPI</el-menu-item>
        </el-submenu>
        <el-submenu index=" 1-2">
          <template slot="title">中国人民银行货币政策司</template>
          <el-menu-item index="1-2-1" title="汇率-USD/EUR" @click="handleClick">Exchange Rate</el-menu-item>
        </el-submenu>
      </el-submenu>
      <el-submenu index="2">
        <template slot="title"><i class="el-icon-message"></i>物料价格</template>
        <el-submenu index="2-1">
          <template slot="title">塑膜网</template>
          <el-menu-item index="2-1-1" title="日评">PP</el-menu-item>
          <el-menu-item index="2-1-2" title="日评">PE</el-menu-item>
          <el-menu-item index="2-1-3" title="日评">原油</el-menu-item>
        </el-submenu>
        <el-submenu index="2-2">
          <template slot="title">ICIS</template>
          <el-menu-item index="2-2-1" title="日评">PP</el-menu-item>
        </el-submenu>
        <el-submenu index="2-3">
          <template slot="title">卓创资讯</template>
          <el-menu-item index="2-1-1" title="日评">聚乙烯LLDPE</el-menu-item>
        </el-submenu>
        <el-submenu index="2-4">
          <template slot="title">新浪财经</template>
          <el-menu-item index="2-1-1" title="日K线">聚丙烯PP0期货</el-menu-item>
          <el-menu-item index="2-1-2" title="日K线">PTA连续期货</el-menu-item>
        </el-submenu>
      </el-submenu>
       <el-submenu index="3">
        <template slot="title"><i class="el-icon-message"></i>成品价格</template>
        <el-submenu index="3-1">
          <template slot="title">塑膜网</template>
          <el-menu-item index="3-1-1" title="日评">BOPP</el-menu-item>
          <el-menu-item index="3-1-2" title="日评">BOPET</el-menu-item>
           <el-menu-item index="3-1-3" title="日评">CPP</el-menu-item>
        </el-submenu>
      </el-submenu>
    </el-menu>
  </el-aside>
  
  <el-container>
    <el-header style="text-align: center; font-size: 20px">
      <!-- <el-dropdown>
        <i class="el-icon-setting" style="margin-right: 15px"></i>
        <el-dropdown-menu slot="dropdown">
          <el-dropdown-item>查看</el-dropdown-item>
          <el-dropdown-item>新增</el-dropdown-item>
          <el-dropdown-item>删除</el-dropdown-item>
        </el-dropdown-menu>
      </el-dropdown> -->
      <span>汇率ER</span>
    </el-header>
    
    <el-main>
      <!-- <div>
        {{tableData[1]}}
      </div> -->
      <el-table :data="tableData" 
      height="300"
      :default-sort = "{prop: 'date', order: 'descending'}">
        <el-table-column prop="date" label="日期" sortable width="300">
        </el-table-column>
        <el-table-column prop="usd" label="1美元兑人民币" sortable width="300">
        </el-table-column>
        <el-table-column prop="eur" label="1欧元兑人民币">
        </el-table-column>
      </el-table>
    </el-main>
  </el-container>
  <el-container>
    
  </el-container>
</el-container>
</template>

<script>

export default {
    data() {
      return {
        tableData:[]
      }
    },
    methods:{
      handleClick(){
        var xhr = new XMLHttpRequest()  //创建一个对象
        xhr.open('GET','/汇率ER.json',false)  //设置ajax，.open()方法里面的三个参数分别是：要发送的请求类型、请求的url、表示是否异步发送请求的布尔值
        xhr.send()  //发出请求
        this.tableData = eval(xhr.responseText)
      }
    }
  }
</script>

<style>
  .el-header {
    background-color: #B3C0D1;
    color: #333;
    line-height: 60px;
  }
  
  .el-aside {
    color: #333;
  }
/* .container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
} */
</style>
