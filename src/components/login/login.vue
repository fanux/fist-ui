<style lang="less">
  @import './login.less';
</style>
<template>
	<div class="login">
		<div class="from-wrap">
			<h2>登录</h2>
			<Form ref="loginData" :model="loginData" :rules="ruleValidate" :label-width="80">
				<FormItem label="用户名" prop="acct">
		            <Input type="password" v-model="loginData.acct" placeholder="请输入用户名"></Input>
		        </FormItem>
		        <FormItem label="密码" prop="pass">
		            <Input type="password" v-model="loginData.pass" placeholder="请输入密码"></Input>
		        </FormItem>
		        <FormItem class="form-footer">
		            <Button type="primary" @click="handleSubmit('loginData')">登录</Button>
		            <Button type="ghost" @click="handleReset('loginData')" style="margin-left: 8px">取消</Button>
		        </FormItem>
			</Form>
		</div>
	</div>
</template>
<script>
export default {
  data () {
    return {
      loginData: {
      	acct:'',
      	pass:''
      },
      ruleValidate: {
      	acct: [
            { required: true, message: '账号不能为空', trigger: 'blur' },
            { min: 3, max: 16, message: '账号长度3-16个字符', trigger: 'blur' }
        ],
        pass: [
            { required: true, message: '密码不能为空', trigger: 'blur' },
            { type: 'string', min: 6, max: 16, message: '密码长度6-16个字符', trigger: 'blur' }
        ]
      }
    }
  },
  methods: {
    handleSubmit (name) {
      this.$refs[name].validate((valid) => {
        if (valid) {
          this.$Message.success('提交成功!')
        } else {
          this.$Message.error('表单验证失败!')
        }
      })
    },
    handleReset (name) {
        this.$refs[name].resetFields();
    }
  }
}
</script>
