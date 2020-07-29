<template>
  <el-container>
    <el-header  >Microsoft</el-header>

    <el-main>
      <div class="box">
        <el-form :model="ruleForm" :rules="rules" ref="ruleForm" label-width="200px" class="demo-ruleForm">
          <!--          <el-form-item label="Activation Date:" prop="ActivationDate">-->
          <!--            <el-date-picker type="date" placeholder="Activation Date" v-model="ruleForm.date1" style="width: 100%;"></el-date-picker>-->
          <!--          </el-form-item>-->


          <!--          <el-form-item label="Expired Date:" prop="ExpiredDate">-->
          <!--            <el-time-picker placeholder="Expired Date" v-model="ruleForm.date2" style="width: 100%;"></el-time-picker>-->
          <!--          </el-form-item>-->


          <!--          <el-form-item label="Organization Name:" prop="OrganizationName">-->
          <!--            <el-input v-model="ruleForm.OrganizationName"></el-input>-->
          <!--          </el-form-item>-->
          <!--          <el-form-item label="PAT Name:" prop="PATName">-->
          <!--            <el-input v-model="ruleForm.PATName"></el-input>-->
          <!--          </el-form-item>-->
          <!--          <el-form-item label="Scope:" prop="Scope">-->
          <!--            <el-input v-model="ruleForm.Scope"></el-input>-->
          <!--          </el-form-item>-->
          <!--          <el-form-item label="Account:" prop="Account">-->
          <!--            <el-input v-model="ruleForm.Account"></el-input>-->
          <!--          </el-form-item>-->
          <!--          <el-form-item label="URL:" prop="URL">-->
          <!--            <el-input v-model="ruleForm.URL"></el-input>-->
          <!--          </el-form-item>-->
          <!--          <el-form-item label="Secret Name:" prop="SecretName">-->
          <!--            <el-input v-model="ruleForm.SecretName"></el-input>-->
          <!--          </el-form-item>-->
          <!--          <el-form-item label="Code Dependency:">-->
          <!--            <el-select v-model="ruleForm.CodeDependency" placeholder="Choose Code Dependency">-->
          <!--              <el-option label="YES" value="YES"></el-option>-->
          <!--              <el-option label="NO" value="NO"></el-option>-->
          <!--            </el-select>-->
          <!--          </el-form-item>-->
          <el-form-item label="The URL you copied from:" prop="CopyUrl">
            <el-input v-model="ruleForm.SecretName"></el-input>
          </el-form-item>
          <el-form-item label="The new secret URL in AKV:" prop="SecretUrl">
            <el-input v-model="ruleForm.SecretName"></el-input>
          </el-form-item>
          <el-form-item label="The new secret name in AKV:" prop="SecretName">
            <el-input v-model="ruleForm.SecretName"></el-input>
          </el-form-item>
          <el-form-item label="Code Dependency:">
            <el-select v-model="ruleForm.CodeDependency" placeholder="Choose Code Dependency">
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
        ruleForm: {
          // ActivationDate: '',
          // ExpiredDate: '',
          // OrganizationName: '',
          // PATName:"",
          // Scope:"",
          // Account:"",
          // URL:"",
          CopyUrl:"",
          SecretUrl:"",
          SecretName:"",
          CodeDependency:"",

        },
        rules: {
          name: [
            { required: true, message: '请输入活动名称', trigger: 'blur' },
            { min: 3, max: 5, message: '长度在 3 到 5 个字符', trigger: 'blur' }
          ],
          region: [
            { required: true, message: '请选择活动区域', trigger: 'change' }
          ],
          date1: [
            { type: 'date', required: true, message: '请选择日期', trigger: 'change' }
          ],
          date2: [
            { type: 'date', required: true, message: '请选择时间', trigger: 'change' }
          ],
          type: [
            { type: 'array', required: true, message: '请至少选择一个活动性质', trigger: 'change' }
          ],
          resource: [
            { required: true, message: '请选择活动资源', trigger: 'change' }
          ],
          desc: [
            { required: true, message: '请填写活动形式', trigger: 'blur' }
          ]
        }
      };
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
    /*background-color: bisque;*/
  }
</style>
