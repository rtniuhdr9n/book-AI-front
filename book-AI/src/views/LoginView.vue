<template>
  <div class="auth-container">
    <div class="auth-form">
      <h1 class="title">BookAI</h1>
      <h2 class="subtitle">登录</h2>
      
      <form @submit.prevent="handleLogin">
        <div class="input-group">
          <label for="username">邮箱/用户名</label>
          <input 
            id="username" 
            v-model="loginForm.username" 
            type="text" 
            placeholder="请输入邮箱或用户名"
            required
          />
        </div>
        
        <div class="input-group">
          <label for="password">密码</label>
          <input 
            id="password" 
            v-model="loginForm.password" 
            type="password" 
            placeholder="请输入密码"
            required
          />
        </div>
        
        <button type="submit" class="submit-button">登录</button>
      </form>
      
      <p class="redirect-text">
        还没有账户？
        <router-link to="/register" class="link">立即注册</router-link>
      </p>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import { useRouter } from 'vue-router';

interface LoginForm {
  username: string;
  password: string;
}

const router = useRouter();
const loginForm = ref<LoginForm>({
  username: '',
  password: ''
});

const handleLogin = async () => {
  // 模拟登录请求
  console.log('登录信息:', loginForm.value);
  
  // 模拟API调用延迟
  await new Promise(resolve => setTimeout(resolve, 1000));
  
  // 模拟登录成功
  console.log('登录成功！');
  alert('登录成功！');
  
  // 登录成功后跳转到首页
  router.push('/');
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

.submit-button {
  width: 100%;
  padding: 0.75rem;
  background-color: #409eff;
  color: white;
  border: none;
  border-radius: 4px;
  font-size: 1rem;
  cursor: pointer;
  transition: background-color 0.3s;
  margin-top: 1rem;
}

.submit-button:hover {
  background-color: #66b1ff;
}

.submit-button:active {
  background-color: #3a7bc8;
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