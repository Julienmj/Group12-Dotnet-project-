<template>
  <div class="auth-wrapper">
    <!-- Animated Background -->
    <div class="animated-bg">
      <div class="shape shape-1"></div>
      <div class="shape shape-2"></div>
      <div class="shape shape-3"></div>
      <div class="shape shape-4"></div>
      <div class="shape shape-5"></div>
    </div>

    <div class="auth-card">
      <div class="auth-logo">
        <svg class="logo-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"></path>
          <circle cx="12" cy="10" r="3"></circle>
        </svg>
        EventLocal
      </div>
      <h2>Create account</h2>
      <p class="auth-sub">Join your local community today</p>

      <form @submit.prevent="handleRegister">
        <div class="form-group">
          <label>Username</label>
          <div class="input-with-icon">
            <svg class="input-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2"></path>
              <circle cx="12" cy="7" r="4"></circle>
            </svg>
            <input v-model="form.username" type="text" placeholder="Choose a username" required />
          </div>
        </div>
        <div class="form-group">
          <label>Email</label>
          <div class="input-with-icon">
            <svg class="input-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"></path>
              <polyline points="22,6 12,13 2,6"></polyline>
            </svg>
            <input v-model="form.email" type="email" placeholder="Enter your email" required />
          </div>
        </div>
        <div class="form-group">
          <label>Password</label>
          <div class="input-wrap">
            <svg class="input-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <rect x="3" y="11" width="18" height="11" rx="2" ry="2"></rect>
              <path d="M7 11V7a5 5 0 0 1 10 0v4"></path>
            </svg>
            <input v-model="form.password" :type="showPass ? 'text' : 'password'" placeholder="Create a password" required />
            <button type="button" class="toggle-pass" @click="showPass = !showPass">
              <svg v-if="showPass" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                <path d="M17.94 17.94A10.07 10.07 0 0 1 12 20c-7 0-11-8-11-8a18.45 18.45 0 0 1 5.06-5.94M9.9 4.24A9.12 9.12 0 0 1 12 4c7 0 11 8 11 8a18.5 18.5 0 0 1-2.16 3.19m-6.72-1.07a3 3 0 1 1-4.24-4.24"></path>
                <line x1="1" y1="1" x2="23" y2="23"></line>
              </svg>
              <svg v-else viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                <path d="M1 12s4-8 11-8 11 8 11 8-4 8-11 8-11-8-11-8z"></path>
                <circle cx="12" cy="12" r="3"></circle>
              </svg>
            </button>
          </div>
        </div>
        <div class="form-group">
          <label>I want to</label>
          <div class="role-options">
            <label
              v-for="role in roles"
              :key="role.value"
              :class="['role-card', { active: form.role === role.value }]"
            >
              <input type="radio" v-model="form.role" :value="role.value" hidden />
              <div class="role-icon" v-html="role.icon"></div>
              <span class="role-label">{{ role.label }}</span>
            </label>
          </div>
        </div>

        <div v-if="error" class="error-msg">{{ error }}</div>
        <div v-if="success" class="success-msg">Account created! Redirecting to login...</div>

        <button type="submit" class="btn-primary submit-btn" :disabled="loading">
          {{ loading ? 'Creating account...' : 'Create Account' }}
        </button>
      </form>

      <p class="auth-switch">
        Already have an account? <router-link to="/login">Sign in</router-link>
      </p>
    </div>
  </div>
</template>

<script setup>
import { ref, reactive } from 'vue'
import { useRouter } from 'vue-router'
import api from '../api'

const router = useRouter()
const form = reactive({ username: '', email: '', password: '', role: 'Attendee' })
const loading = ref(false)
const error = ref('')
const success = ref(false)
const showPass = ref(false)

const roles = [
  { 
    value: 'Attendee', 
    label: 'Attend Events', 
    icon: '<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2"></path><circle cx="12" cy="7" r="4"></circle></svg>'
  },
  { 
    value: 'Organizer', 
    label: 'Organize Events', 
    icon: '<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M22 19a2 2 0 0 1-2 2H4a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2h5l2 3h9a2 2 0 0 1 2 2z"></path></svg>'
  },
]

async function handleRegister() {
  loading.value = true
  error.value = ''
  try {
    await api.post('/auth/register', form)
    success.value = true
    setTimeout(() => router.push('/login'), 1500)
  } catch (e) {
    error.value = e.response?.data?.message || 'Registration failed. Please try again.'
  } finally {
    loading.value = false
  }
}
</script>

<style scoped>
.auth-wrapper {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  overflow: hidden;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}

/* Animated Background */
.animated-bg {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  overflow: hidden;
  z-index: 1;
}

.shape {
  position: absolute;
  border-radius: 50%;
  filter: blur(60px);
  opacity: 0.5;
  animation: float 20s infinite ease-in-out;
}

.shape-1 {
  width: 400px;
  height: 400px;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  top: -100px;
  left: -100px;
  animation-delay: 0s;
}

.shape-2 {
  width: 350px;
  height: 350px;
  background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
  top: 50%;
  right: -100px;
  animation-delay: 2s;
}

.shape-3 {
  width: 300px;
  height: 300px;
  background: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%);
  bottom: -100px;
  left: 30%;
  animation-delay: 4s;
}

.shape-4 {
  width: 250px;
  height: 250px;
  background: linear-gradient(135deg, #43e97b 0%, #38f9d7 100%);
  top: 20%;
  right: 25%;
  animation-delay: 6s;
}

.shape-5 {
  width: 200px;
  height: 200px;
  background: linear-gradient(135deg, #fa709a 0%, #fee140 100%);
  bottom: 20%;
  right: 40%;
  animation-delay: 8s;
}

@keyframes float {
  0%, 100% {
    transform: translate(0, 0) scale(1);
  }
  25% {
    transform: translate(50px, -50px) scale(1.1);
  }
  50% {
    transform: translate(-30px, 30px) scale(0.9);
  }
  75% {
    transform: translate(40px, 40px) scale(1.05);
  }
}

.auth-card {
  position: relative;
  z-index: 2;
  width: 100%;
  max-width: 440px;
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(20px);
  border-radius: 24px;
  padding: 48px 40px;
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
  animation: slideUp 0.6s ease-out;
  max-height: 95vh;
  overflow-y: auto;
}

@keyframes slideUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.auth-logo { 
  font-size: 18px; 
  font-weight: 700; 
  color: var(--blue); 
  margin-bottom: 36px;
  display: flex;
  align-items: center;
  gap: 8px;
}

.logo-icon {
  width: 24px;
  height: 24px;
  flex-shrink: 0;
}

.auth-card h2 { font-size: 28px; font-weight: 700; margin-bottom: 6px; }
.auth-sub { color: var(--muted); font-size: 14px; margin-bottom: 32px; }

.form-group { display: flex; flex-direction: column; gap: 6px; margin-bottom: 18px; }
.form-group label { font-size: 13px; font-weight: 600; color: var(--text); }

.input-with-icon {
  position: relative;
}

.input-with-icon input {
  padding: 11px 14px 11px 42px;
  border: 1px solid var(--border);
  border-radius: 10px;
  font-size: 14px;
  font-family: 'Inter', sans-serif;
  outline: none;
  transition: border 0.2s;
  width: 100%;
}

.input-with-icon input:focus {
  border-color: var(--blue);
}

.input-icon {
  position: absolute;
  left: 12px;
  top: 50%;
  transform: translateY(-50%);
  width: 18px;
  height: 18px;
  color: var(--muted);
  pointer-events: none;
}

.form-group input, .input-wrap input {
  padding: 11px 14px 11px 42px;
  border: 1px solid var(--border);
  border-radius: 10px;
  font-size: 14px;
  font-family: 'Inter', sans-serif;
  outline: none;
  transition: border 0.2s;
  width: 100%;
}

.form-group input:focus, .input-wrap input:focus { border-color: var(--blue); }

.input-wrap { position: relative; }

.toggle-pass {
  position: absolute;
  right: 12px;
  top: 50%;
  transform: translateY(-50%);
  background: none;
  border: none;
  cursor: pointer;
  padding: 4px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: var(--muted);
  transition: color 0.2s;
}

.toggle-pass:hover {
  color: var(--blue);
}

.toggle-pass svg {
  width: 18px;
  height: 18px;
}

.role-options { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; }

.role-card {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 8px;
  padding: 16px;
  border: 2px solid var(--border);
  border-radius: 10px;
  cursor: pointer;
  transition: all 0.2s;
}

.role-card.active { border-color: var(--blue); background: #e8f4fd; }

.role-icon { 
  width: 28px;
  height: 28px;
  color: var(--blue);
  display: flex;
  align-items: center;
  justify-content: center;
}

.role-icon svg {
  width: 100%;
  height: 100%;
}

.role-label { font-size: 12px; font-weight: 600; color: var(--text); }

.error-msg {
  background: #fff0f0;
  color: #e0245e;
  border-radius: 8px;
  padding: 10px 14px;
  font-size: 13px;
  margin-bottom: 16px;
}

.success-msg {
  background: #f0fff4;
  color: #16a34a;
  border-radius: 8px;
  padding: 10px 14px;
  font-size: 13px;
  margin-bottom: 16px;
}

.submit-btn { width: 100%; padding: 13px; font-size: 15px; border-radius: 10px; margin-top: 4px; }
.submit-btn:disabled { opacity: 0.6; cursor: not-allowed; }

.auth-switch { text-align: center; font-size: 13px; color: var(--muted); margin-top: 24px; }
.auth-switch a { color: var(--blue); font-weight: 600; }

@media (max-width: 768px) {
  .auth-card { 
    margin: 20px;
    padding: 40px 28px; 
  }
  
  .shape {
    filter: blur(40px);
  }
}
</style>
