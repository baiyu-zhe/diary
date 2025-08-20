<template>
  <!-- 重要公告卡片 -->
  <div class="announcement-card" v-if="isVisible">
    <!-- 关闭按钮 -->
<!--    <button class="close-btn" @click="isVisible = false">
      <svg t="1755659636151" class="icon" viewBox="0 0 1027 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="6058" width="200" height="200"><path d="M1002.17475 21.837105a74.286973 74.286973 0 0 0-105.103821 0L513.901173 405.006861 130.629374 21.837105a74.491058 74.491058 0 0 0-105.103821 105.103821L408.797352 510.212725 25.525553 893.382481a74.389015 74.389015 0 1 0 105.103821 105.103821L513.901173 615.316546l383.271799 383.169756a73.878803 73.878803 0 0 0 105.103821 0 74.18493 74.18493 0 0 0 0-105.103821L619.004994 510.212725l383.271799-383.271799a74.286973 74.286973 0 0 0 0-105.103821" fill="#999999" p-id="6059"></path></svg>
    </button>-->

    <!-- 公告头部 -->
    <div class="announcement-header">
      <div class="announcement-tag">
        <span>📢重要公告</span>
      </div>
      <span class="announcement-date">2025-08-20</span>
    </div>

    <!-- 公告内容 -->
    <div class="announcement-content">
      <h3 class="announcement-title">全网最美博客Teek🎉</h3>

      <p class="announcement-text">
        Teek~一款简约、唯美、丝滑且强大的VitePress主题博客(知识库&博客二合一) ，正在持续迭代更新，欢迎交流学习！
      </p>

 

      <!-- 底部操作区 -->
      <div class="announcement-footer">
        <button class="announcement-button" @click="navigateTo('https://vp.teek.top/')">
          <span>查看详情</span>
          <i class="fa fa-arrow-right"></i>
        </button>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import {useRouter, withBase} from "vitepress";
import {isClient} from "vitepress-theme-teek";
const router = useRouter(); // 获取 VitePress 路由实例

// 控制组件显示状态
const isVisible = ref(true);

// 导航到指定路由
const navigateTo = (path: string) => {
  if (!isClient) return null;

  const targetPath = withBase(path);
  router.go(targetPath); // 使用 VitePress 路由的 goTo 方法
};
</script>

<style scoped>
.announcement-card {
  width: var(--tk-home-card-width);
  margin: 0 auto;
  background-color: var(--tk-bg-color-elm);
  border-radius: var(--tk-home-card-border-radius);
  box-shadow: var(--tk-card-shadow);
  overflow: hidden;
  transition: box-shadow var(--tk-transition-duration-slow), transform var(--tk-transition-duration-slow);
  position: relative; /* 为关闭按钮提供定位基准 */
}

.announcement-card:hover {
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.12);
  transform: translateY(-3px);
}

/* 关闭按钮样式 */
.close-btn {
  position: absolute;
  top: 12px;
  right: 12px;
  width: 24px;
  height: 24px;
  border: none;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.2s ease;
  z-index: 10; /* 确保按钮在最上层 */
}

.close-btn:hover {
  color: #dc2626; /*  hover时变红 */
}

.announcement-header {
  background-color: rgba(59, 130, 246, 0.05);
  padding: 16px 24px;
  border-bottom: 1px solid #e5e7eb;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.announcement-tag {
  display: inline-flex;
  align-items: center;
  padding: 4px 12px;
  border-radius: 999px;
  background-color: rgba(249, 115, 22, 0.1);
  color: #F97316;
  font-size: 12px;
  font-weight: 500;
}

.announcement-tag i {
  margin-right: 6px;
}

.announcement-date {
  color: #6b7280;
  font-size: 14px;
}

.announcement-content {
  padding: 20px;
}

.announcement-title {
  margin: 0 0 12px 0;
  font-size: 20px;
  font-weight: 700;
  color: #111827;
  transition: color 0.3s ease;
}

.announcement-card:hover .announcement-title {
  color: #3B82F6;
}

.announcement-text {
  margin: 0 0 16px 0;
  color: #374151;
  line-height: 1.6;
  display: -webkit-box;
  -webkit-line-clamp: 4;
  -webkit-box-orient: vertical;
  overflow: hidden;
}

.announcement-attachment {
  margin: 0 0 10px 0;
  display: flex;
  align-items: center;
  color: #3B82F6;
  font-size: 14px;
}

.announcement-attachment i {
  margin-right: 8px;
}

.announcement-footer {
  padding-top: 16px;
  border-top: 1px solid #f3f4f6;
  display: flex;
  justify-content: end;
  align-items: center;
}

.announcement-button {
  display: inline-flex;
  align-items: center;
  background: none;
  border: none;
  color: #3B82F6;
  font-weight: 500;
  cursor: pointer;
  transition: color 0.2s ease;
  padding: 0;
}

.announcement-button:hover {
  color: #2563eb;
}

.announcement-button i {
  margin-left: 6px;
  font-size: 12px;
}
</style>