<template>
    <div id="twikoo"></div>
  </template>
  
  <script setup lang="ts">
  import { onMounted, watch } from 'vue'
  import { useRoute } from 'vitepress'
  
  const route = useRoute()
  
  const initTwikoo = async () => {
    // 判断是否在浏览器环境中
    if (typeof window !== 'undefined') {
      const twikoo = await import('twikoo') 
      twikoo.init({
        envId: 'https://twikoo.onedayxyy.cn/', // 换成你自己配置的域名
        el: '#twikoo'
      })
    }
  }
  
  // 监听路由刷新评论
  watch(route, () => {
    initTwikoo()
  })
  
  onMounted(() => {
    initTwikoo()
  })
  </script>