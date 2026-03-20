<template>
  <div class="login-container">
    <div class="login-form">
      <h1 class="title">BookAI</h1>
      <form @submit.prevent="handleLogin">
        <div class="input-group">
          <label for="username">邮箱/用户名</label>
          <input 
            id="username" 
            v-model="username" 
            type="text" 
            placeholder="请输入邮箱或用户名"
            required
          />
        </div>
        
        <div class="input-group">
          <label for="password">密码</label>
          <input 
            id="password" 
            v-model="password" 
            type="password" 
            placeholder="请输入密码"
            required
          />
        </div>
        
        <button type="submit" class="login-button">登录</button>
      </form>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const username = ref('');
const password = ref('');

const handleLogin = () => {
  // 这里可以添加登录逻辑
  console.log('登录信息:', { username: username.value, password: password.value });
  alert(`欢迎回来 ${username.value}！登录功能已提交`);
};
</script>

<style scoped>
.login-container {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  background-color: #f5f5f5;
}

.login-form {
  width: 100%;
  max-width: 400px;
  padding: 2rem;
  background-color: white;
  border-radius: 8px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}

.title {
  text-align: center;
  margin-bottom: 1.5rem;
  color: #333;
  font-size: 2rem;
  font-weight: bold;
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

.login-button {
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

.login-button:hover {
  background-color: #66b1ff;
}

.login-button:active {
  background-color: #3a7bc8;
}
</style>