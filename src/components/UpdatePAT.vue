<template>
  <el-container>
    <el-header>UpdatePAT</el-header>
    <el-main>
      <el-form :model="ruleForm" :rules="rules" ref="ruleForm" label-width="200px" class="demo-ruleForm">
        <el-form-item label="New PAT Name" prop="name" style="width:50%;">
          <el-input v-model="ruleForm.name"></el-input>
        </el-form-item>

        <el-form-item label="New Expired Date" required>
        <el-col :span="11">
          <el-form-item prop="date1">
            <el-date-picker type="date" placeholder="Choose Date" v-model="ruleForm.date1" style="width: 100%;"></el-date-picker>
          </el-form-item>
        </el-col>
        </el-form-item>
        <el-form-item label="New Activation Date" required>
          <el-col :span="11">
            <el-form-item prop="date2">
              <el-date-picker type="date" placeholder="Choose Date" v-model="ruleForm.date1" style="width: 100%;"></el-date-picker>
            </el-form-item>
          </el-col>
        </el-form-item>
        <el-form-item>
          <el-button type="primary" @click="submitForm('ruleForm')">NEXT</el-button>
          <el-button @click="resetForm('ruleForm')">RESET</el-button>
        </el-form-item>
      </el-form>
    </el-main>
  </el-container>

</template>


<script>
  export default {
    name: "UpdatePAT",
    data(){
      return{
        NewPatName:"",
        ExpiredDate:"",
        ActivationDate:"",
        ruleForm: {
          name: '',
          date1: '',
          date2: '',
        }
      }
    },
    methods: {
      submitForm(formName) {
        this.$refs[formName].validate((valid) => {
          if (valid) {
            alert('submit!');
          } else {
            console.log('error submit!!');
            return false;
          }
        });
      },
      resetForm(formName) {
        this.$refs[formName].resetFields();
      }
    }
  }
</script>

<style>
  .el-header, .el-footer {
    background-color: #B3C0D1;
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
</style>
