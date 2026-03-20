<template>
  <div class="auth-container">
    <div class="auth-form">
      <h1 class="title">BookAI</h1>
      <h2 class="subtitle">用户注册</h2>
      
      <form @submit.prevent="handleRegister">
        <div class="input-group">
          <label for="reg-username">用户名</label>
          <input 
            id="reg-username" 
            v-model="registerForm.username" 
            type="text" 
            placeholder="请输入用户名"
            required
          />
        </div>
        
        <div class="input-group">
          <label for="reg-email">邮箱</label>
          <input 
            id="reg-email" 
            v-model="registerForm.email" 
            type="email" 
            placeholder="请输入邮箱地址"
            required
          />
        </div>
        
        <div class="input-group">
          <label for="reg-password">密码</label>
          <input 
            id="reg-password" 
            v-model="registerForm.password" 
            type="password" 
            placeholder="请输入密码"
            required
          />
        </div>
        
        <div class="input-group">
          <label for="confirm-password">确认密码</label>
          <input 
            id="confirm-password" 
            v-model="confirmPassword" 
            type="password" 
            placeholder="请再次输入密码"
            :class="{ 'error': passwordMismatch }"
            required
          />
          <span v-if="passwordMismatch" class="error-message">{{ passwordMismatch }}</span>
        </div>
        
        <button type="submit" class="submit-button">注册</button>
      </form>
      
      <p class="redirect-text">
        已有账户？
        <router-link to="/login" class="link">立即登录</router-link>
      </p>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue';
import { useRouter } from 'vue-router';

interface RegisterForm {
  username: string;
  email: string;
  password: string;
}

const router = useRouter();
const registerForm = ref<RegisterForm>({
  username: '',
  email: '',
  password: ''
});
const confirmPassword = ref('');

const passwordMismatch = computed(() => {
  if (confirmPassword.value && registerForm.value.password !== confirmPassword.value) {
    return '两次输入的密码不一致';
  }
  return '';
});

const handleRegister = async () => {
  // 基础表单验证
  if (!registerForm.value.username || !registerForm.value.email || !registerForm.value.password) {
    alert('请填写所有必填字段');
    return;
  }

  if (passwordMismatch.value) {
    alert(passwordMismatch.value);
    return;
  }

  // 模拟注册请求
  console.log('注册信息:', {
    username: registerForm.value.username,
    email: registerForm.value.email,
    password: registerForm.value.password
  });

  // 模拟API调用延迟
  await new Promise(resolve => setTimeout(resolve, 1000));

  // 模拟注册成功
  console.log('注册成功！');
  alert('注册成功！');

  // 注册完成后跳转到登录页
  router.push('/login');
};
</script>

<style scoped>
.auth-container {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  background-color: #f5f5f5;
}

.auth-form {
  width: 100%;
  max-width: 400px;
  padding: 2rem;
  background-color: white;
  border-radius: 8px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}

.title {
  text-align: center;
  margin-bottom: 0.5rem;
  color: #333;
  font-size: 2rem;
  font-weight: bold;
}

.subtitle {
  text-align: center;
  margin-bottom: 1.5rem;
  color: #666;
  font-size: 1.2rem;
}

.input-group {
  margin-bottom: 1rem;
}

.input-group label {
  display: block;
  margin-bottom: 0.5rem;
  color: #555;
  font-weight: 500;
}

.input-group input {
  width: 100%;
  padding: 0.75rem;
  border: 1px solid #ddd;
  border-radius: 4px;
  font-size: 1rem;
  transition: border-color 0.3s;
  box-sizing: border-box;
}

.input-group input:focus {
  outline: none;
  border-color: #409eff;
  box-shadow: 0 0 0 2px rgba(64, 158, 237, 0.2);
}

.input-group input.error {
  border-color: #f56c6c;
}

.error-message {
  color: #f56c6c;
  font-size: 0.8rem;
  display: block;
  margin-top: 0.3rem;
}

.submit-button {
  width: 100%;
  padding: 0.75rem;
  background-color: #67c23a;
  color: white;
  border: none;
  border-radius: 4px;
  font-size: 1rem;
  cursor: pointer;
  transition: background-color 0.3s;
  margin-top: 1rem;
}

.submit-button:hover {
  background-color: #85ce61;
}

.submit-button:active {
  background-color: #5daf34;
}

.redirect-text {
  text-align: center;
  margin-top: 1.5rem;
  color: #666;
}

.link {
  color: #409eff;
  text-decoration: none;
  cursor: pointer;
}

.link:hover {
  text-decoration: underline;
}
</style>