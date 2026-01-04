<template>
  <div class="background"></div>
  <Home />
  <footer class="site-footer">
    <!-- 站点版权 -->
    <div class="footer-item">
      © 2025 Made in <a href="/" target="_blank">{{ userName }}</a>
    </div>

    <!-- ICP备案号 -->
    <div class="footer-item" v-if="icpNumber">
      <a
        :href="`https://icp.gov.moe/?keyword=${icpNumber}`"
        target="_blank"
        class="icp-link"
        rel="noopener noreferrer"
      >
        ✮{{ icpNumber }}✮
      </a>
    </div>

    <!-- 公安备案号 -->
    <div class="footer-item" v-if="policenumber">
      <a
        :href="`https://beian.mps.gov.cn/#/query/webSearch?police=${policenumber}`"
        target="_blank"
        class="police-link"
        rel="noopener noreferrer"
      >
        <span class="police-img"></span>
        {{ policenumber }}
      </a>
    </div>
  </footer>
</template>

<script setup>
import { ref } from 'vue';
import Home from './components/Home.vue';

// 用户名、ICP备案号、公安备案号从环境变量读取，默认值可直接替换
const userName = ref(import.meta.env.VITE_APP_USER_NAME || '你的站名');
const icpNumber = ref(import.meta.env.VITE_APP_ICP_NUMBER || '20260033'); // 默认萌ICP备20260033号
const policenumber = ref(import.meta.env.VITE_APP_POLICE_NUMBER || ''); // 如无公安备案可留空
</script>

<style scoped>
/* 页脚整体样式 */
.site-footer {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  gap: 15px;
  padding: 20px;
  font-size: 14px;
  background-color: #f9f9f9;
  color: #555;
  border-top: 1px solid #e5e5e5;
}

/* 页脚每个单独元素 */
.footer-item {
  display: flex;
  align-items: center;
}

/* 所有链接样式 */
.site-footer a {
  color: #555;
  text-decoration: none;
  transition: color 0.2s;
}

.site-footer a:hover {
  color: #0078ff;
  text-decoration: underline;
}

/* ICP备案号样式 */
.icp-link {
  font-weight: bold;
}

/* 公安备案号样式 */
.police-link {
  display: flex;
  align-items: center;
}

/* 公安备案图标 */
.police-img {
  display: inline-block;
  width: 18px;
  height: 18px;
  background: url('/police-icon.png') no-repeat center center;
  background-size: contain;
  margin-right: 5px;
}

/* 手机端适配 */
@media (max-width: 600px) {
  .site-footer {
    flex-direction: column;
    gap: 8px;
    font-size: 12px;
  }
}
</style>
