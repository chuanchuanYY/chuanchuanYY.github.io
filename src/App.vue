<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
import { ElButton } from 'element-plus';
import {ref} from 'vue'
const dialogVisible =ref(false);

const onClick = function()
{
  dialogVisible.value = !dialogVisible.value;
  fetchFileContent();
}
async function fetchFileContent() {
            const owner = 'chaunchuanYY'; // 替换为你的 GitHub 用户名
            const repo = 'chuanchuanYY.github.io'; // 替换为你的仓库名
            const path = 'assetrs/反转链表.md'; // 替换为你的文件路径
            const url = `https://github.com/${owner}/${repo}/blob/main/${path}`;

            try {
                const response = await fetch(url);
                const data = await response.json();
                const content = atob(data.content); // 解码 Base64 内容
                document.getElementById('fileContent').textContent = content;
            } catch (error) {
                console.error('Error fetching file content:', error);
            }
        }
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <pre id="fileContent"></pre>
      <HelloWorld msg="You did it! CHUAN" />
      <el-button type="primary" v-on:click="onClick">ShowDialog</el-button>

      <el-dialog
      v-model="dialogVisible"
      title="Tips"
      width="500"
    >
    
      <h1>github action workflow publish success!</h1>
      <h2>黄楚盈！！！👋</h2>
      <span>Hello chuan My Github</span>
    </el-dialog>
      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
