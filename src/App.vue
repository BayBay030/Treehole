<!-- 我是樹洞 Vite + Vue 移植版本，保留原始風格與互動邏輯，適配行動裝置 -->

<template>
  <div>
    <!-- 魔法日記 -->
    <div class="diary-frame">
      <iframe src="https://baybox.neocities.org/Treehole/Magicdiary" scrolling="yes"></iframe>
    </div>

    <!-- 花花封面 -->
    <iframe 
      id="floating-cover"
      frameborder="0"
      scrolling="no"
      allowtransparency="true"
      loading="lazy"
      :src="coverUrl"
    ></iframe>

    <!-- 歷史按鈕 -->
    <div class="hotspot-img effect-dark" style="top: 780px; left: 50px;" @click="toggleHistory">
      <img src="image/magic.gif" alt="Magic TV" style="width: 120px;">
    </div>

    <!-- 引言 -->
    <div class="quote-box leaf" style="top: 60px; left: 120px; background-size: 300px auto;">
      「如果你今天說了一句<br>沒人聽見的話，<br>這棵樹會聽。」
    </div>
    <div class="quote-box cloud" style="top: 310px; left: 650px;background-size: 300px auto;">
      也許過陣子回來看他<br>會變成不一樣的樣子！
    </div>

    <!-- 表單 modal -->
    <div class="modal" v-show="formVisible">
      <div class="close-btn" @click="formVisible = false">✖</div>
      <iframe :src="formUrl"></iframe>
    </div>

    <!-- 歷史 modal -->
    <div class="floating-history" v-show="historyVisible">
      <div class="close-btn" @click="historyVisible = false">✖</div>
      <iframe title="Treehole History" scrolling="yes" loading="lazy" :src="historyUrl"></iframe>
    </div>

    <!-- 開樹洞入口 -->
    <div class="treehole-button" @click="toggleForm">
      點我開樹洞
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const formVisible = ref(false)
const historyVisible = ref(false)
const formUrl = 'https://tally.so/r/wA5N2e'
const historyUrl = 'https://baybox.neocities.org/Treehole/history'
const coverUrl = 'https://baybox.neocities.org/Treehole/cover'

const toggleForm = () => {
  formVisible.value = !formVisible.value
}
const toggleHistory = () => {
  historyVisible.value = !historyVisible.value
}
</script>

<style scoped>
.treehole-button {
  position: fixed;
  bottom: 20px;
  left: 50%;
  transform: translateX(-50%);
  padding: 12px 20px;
  background: #ffe0f7;
  border: 2px solid #ffb3e6;
  border-radius: 24px;
  box-shadow: 0 0 10px rgba(0,0,0,0.1);
  font-size: 16px;
  font-weight: bold;
  color: #6c3365;
  cursor: pointer;
  z-index: 999;
}

.diary-frame, .floating-history, .modal {
  max-width: 90vw;
  margin: 10px auto;
  border-radius: 12px;
  overflow: hidden;
  background: rgba(255, 255, 255, 0.95);
  box-shadow: 0 0 12px #e8a3dc, 0 0 20px #cecece;
}

.modal iframe,
.floating-history iframe,
.diary-frame iframe,
#floating-cover {
  width: 100%;
  height: 100%;
  border: none;
}

.quote-box {
  text-align: center;
  font-size: 1rem;
  color: #5d476a;
  margin: 20px auto;
  max-width: 80vw;
  text-shadow: 0 1px 2px rgba(255,255,255,0.7);
}
</style>
