<template>
<el-container>
  <el-header></el-header>
  <el-container>
    <el-aside width="200px">
			<tree></tree>
		</el-aside>
    <el-container>
      <el-main></el-main>
      <el-footer></el-footer>
    </el-container>
  </el-container>
</el-container>
</template>

<script>
import tree from "./Tree.vue";
export default {
	components:{tree},
  name: 'Header',
  data () {
    return {

    }
			
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .el-header, .el-footer {
    background-color:#FFF;
		border:1px solid red;
    color: #333;
    text-align: center;
    line-height: 60px;
  }
  
  .el-aside {
    background-color: #FFF;
    color: #333;
		border:1px solid red;
    text-align: center;
  }
  
  .el-main {
    background-color:#FFF;
    color: #333;
		border:1px solid red;
    text-align: center;
    line-height: 160px;
  }
  
  body > .el-container {
    margin-bottom: 40px;
  }
	.el-container{
		height: 100%;
		width: 100%;
	}
  
  .el-container:nth-child(5) .el-aside,
  .el-container:nth-child(6) .el-aside {
    line-height: 260px;
  }
  
  .el-container:nth-child(7) .el-aside {
    line-height: 320px;
  }
</style>
