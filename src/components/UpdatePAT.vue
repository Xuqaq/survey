<template>
  <el-container>
    <el-header  >Microsoft</el-header>

    <el-main>
      <div class="box">
        <el-form :model="ruleForm" :rules="rules" ref="ruleForm" label-width="500px" class="demo-ruleForm">

          <div class="easyui-panel" title="URL" style="height: 1000px;width: 1000px;text-align:left" >
            1. Generate a new PAT<br>
            Here're some meta info of the PAT you might need to generate a new PAT:<br>
            <table border="1">
              <tbody>
              <tr>
                <td>Organization Name</td>
                <td>@ViewBag.patInfo.Org</td>
              </tr>
              <tr>
                <td>PAT Name</td>
                <td>@ViewBag.patInfo.Name</td>
              </tr>
              <tr>
                <td>Scope</td>
                <td>@ViewBag.patInfo.Scope</td>
              </tr>
              <tr>
                <td>Account</td>
                <td>@ViewBag.patInfo.Account</td>
              </tr>
              </tbody>
            </table>
            If it's a personal account, please visit <a href="@ViewBag.personalLink">Azure DevOps</a> to update your PAT.<br>
            If it's a service account, please follow <a href="@ViewBag.serviceAccountLink">Visual Studio Personal Access Token Generator Wiki</a> to update your PAT.<br>
            Note: Please copy the PAT because you would need it to update the AKV.<br>
            2. Update the AKV<br>
            You need to update all AKV secrets listed below:<br>
            <div>
              <a href="@(ViewBag.expiredUrl)">@ViewBag.expiredUrl</a><br>
            </div>
            <button id="BtnUpdatePat" onclick="window.open('/ServiceRegister/ToAddAPat?applicationId=@(ViewBag.applicationId)&amp;serviceName=@(ViewBag.serviceName)&amp;expiredUrl=@(ViewBag.expiredUrl)','_blank')">Done</button>
          </div>
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
    line-height: 50px;
  }

  .el-aside {
    background-color: #D3DCE6;
    color: #333;
    text-align: center;
    line-height: 50px;
  }

  .el-main {
    background-color: #E9EEF3;
    color: #333;
    text-align: center;
    line-height: 50px;
  }

  body > .el-container {
    margin-bottom: 40px;
  }

  .el-container:nth-child(5) .el-aside,
  .el-container:nth-child(6) .el-aside {
    line-height: 50px;
  }

  .el-container:nth-child(7) .el-aside {
    line-height: 50px;
  }
  .box{
    width:500px;
    margin: 0 auto;
    /*background-color: bisque;*/
  }
</style>
