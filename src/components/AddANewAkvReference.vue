<template>
  <el-container>
    <el-header  >Microsoft</el-header>

    <el-main>
      <div class="box">
        <el-form ref="form" :model="form"  label-width="150px" style="float:left;"
                 label-position = "left">
          <el-form-item label="Secret URL:" size='small' style="margin-left:10px">
            <el-input v-model="form.SecretURL"></el-input>
          </el-form-item>
          <el-form-item label="Code Dependency:">
            <el-select v-model="form.CodeDependency" placeholder="Choose Code Dependency">
              <el-option label="YES" value="YES"></el-option>
              <el-option label="NO" value="NO"></el-option>
            </el-select>
          </el-form-item>
          <el-form-item>
            <el-button type="primary" @click="onSubmit">NEXT</el-button>
            <el-button>REST</el-button>
          </el-form-item>
        </el-form>

      </div>
    </el-main>

  </el-container>

</template>


<script>
  export default {
    name: "UpdatePAT",
    data() {
      return {
        form: {
          SecretURL: '',
          CodeDependency: '',
          date1: '',
          date2: '',
          delivery: false,
          type: [],
          resource: '',
          desc: ''
        }
      }
    },
    methods: {
      onSubmit() {
        console.log('submit!');
      }
    }
  }
</script>

<style>
  .el-header, .el-footer {
    background-color: #D3DCE6;
    color: #333;
    text-align: center;
    line-height: 60px;
  }

  .el-aside {
    background-color: #D3DCE6;
    color: #333;
    text-align: center;
    line-height: 200px;
  }

  .el-main {
    background-color: #E9EEF3;
    color: #333;
    text-align: center;
    line-height: 160px;
  }

  body > .el-container {
    margin-bottom: 40px;
  }

  .el-container:nth-child(5) .el-aside,
  .el-container:nth-child(6) .el-aside {
    line-height: 260px;
  }

  .el-container:nth-child(7) .el-aside {
    line-height: 320px;
  }
  .box{
    width:500px;
    margin: 0 auto;
    background-color: bisque;
  }
</style>
