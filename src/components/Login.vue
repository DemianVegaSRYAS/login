<template>
    <div class="login_wrap">
        <div class="screen_wrap">
            <div class="fk_cam"></div>
            <!-- <el-form> -->
                <div class="log">
                    <form :model="ruleForm" status-icon :rules="rules" ref="ruleForm" label-width="120px" class="demo-ruleForm">
                            <el-avatar src="https://appsdejoseluis.com/wp-content/uploads/2020/04/face_co.png" class="avat"></el-avatar>
                            <input type="text" v-model="input" class="name" placeholder="USERNAME"/>
                            <input type="password" v-model="ruleForm.pass" autocomplete="off" class="pass" placeholder="PASSWORD"/>
                            <el-button class="btn_log">Login</el-button>
                    </form>
                </div>
            <!-- </el-form> -->
        </div>
        <div class="btn"></div>
    </div>
</template>
<script>
export default {
    name : 'Login',
    data() {

        var validatePass = (rule, value, callback) => {
            if (value === '') {
            callback(new Error('Please input the password'));
            } else {
            if (this.ruleForm.checkPass !== '') {
                this.$refs.ruleForm.validateField('checkPass');
            }
            callback();
            }
        };
        var validatePass2 = (rule, value, callback) => {
            if (value === '') {
            callback(new Error('Please input the password again'));
            } else if (value !== this.ruleForm.pass) {
            callback(new Error('Two inputs don\'t match!'));
            } else {
            callback();
            }
        };
        return {
            ruleForm: {
            pass: '',
            name:'',

            },
            rules: {
            pass: [
                { validator: validatePass, trigger: 'blur' }
            ],
            }
        };
        },
        // methods: {
        // submitForm(formName) {
        //     this.$refs[formName].validate((valid) => {
        //     if (valid) {
        //         alert('submit!');
        //     } else {
        //         console.log('error submit!!');
        //         return false;
        //     }
        //     });
        // },
        // resetForm(formName) {
        //     this.$refs[formName].resetFields();
        // }
        // }
    }
</script>
<style scoped>
.login_wrap{
    height: 82vh;
    width: 300px;
    background-color: rgba(0, 0, 0, 0.71);
    border-radius: 30px;
    padding: 5px;
    border: solid 1px rgba(255, 255, 255, 0.237);
    box-shadow: 20px 17px 115px 32px rgba(0,0,0,1);
    -webkit-box-shadow: 20px 17px 115px 32px rgba(0,0,0,1);
    -moz-box-shadow: 20px 17px 115px 32px rgba(0,0,0,1);
}
.el-form-item__label{
    text-align: center;
}
.screen_wrap{
    /* margin: 5px; */
    border-radius: 30px;
    height: 75vh;
    background-color: rgba(255, 255, 255, 0.345);
    padding-top: 5px;
    display:grid;
    grid-template-rows: 40px auto;
    align-items: center;
    justify-items: center;
}
.btn{
    background-color: rgba(0, 0, 0, 0.183);
    height: 30px;
    width: 30px;
    border-radius: 50%;
    margin: 2px auto;
    border: solid 1px #fff;
}
.fk_cam{
    height: 10px;
    width: 10px;
    border-radius: 50%;
    margin: 2px auto;
    background-color: rgba(0, 0, 0, 0.183);

}
.log{
    height: 100%;
    background-color: transparent;
    padding: 1em;
}
.name{
    margin: 5px;
}
.pass{
    margin: 5px;
}
.avat{
    height: 150px;
    width: 150px;
}
.btn_log{

    margin-top: 1em;
    width: auto;
    background-color: transparent;
}
.btn_log:hover{
    background-color: #009BB7;
    color: white;
}
input{
    padding: 1em;
    border-radius: 10px;
    width: 100%;
    color: rgb(0, 0, 0);
    border-color: transparent;
    height: 3em;
    opacity: 70%;
}
input:focus-visible {
    outline-width: 0;
    font-weight: bold;
    color: #009BB7;
    }
</style>