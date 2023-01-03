<!-- 
Inspiration:
https://stackoverflow.com/questions/73147462/binding-a-media-feed-stream-to-video-element-vue-3-composition-api 
-->



<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'
import PushButton from "./components/PushButton.vue";

const stream = ref(null)
const constraints = {
  audio: false,
  video: true,
  // video: {
    // width: { min: 1024, ideal: 1280, max: 1920 },
    // height: { min: 576, ideal: 720, max: 1080 },
  // },
}

onMounted(async () => {
  stream.value = await navigator.mediaDevices.getUserMedia(constraints)
})

onBeforeUnmount(() => {
  stream.value.getTracks().forEach(track => track.stop())
})
</script>

<template>
  <div class="camera">
    <div class="camera-lens">
      <video :srcObject="stream" autoplay></video>
    </div>
    <div class="push-button-container">
      <PushButton class="push-button" />
    </div>
  </div>
</template>

<style>
* {
  height: 100%;
  width: 100%;
  padding: 0%;
}

#app {
  background: url('assets/camera-background.svg');
  background-size: cover;
}

.push-button-container {
  margin-left: 85%;
}

.push-button {
  width: 100px;
  height: 100px;
}

.camera-lens {
  border: 5px solid rgb(34, 34, 34);
  background-color: black;
  width: 30%;
  height: 30%;
  margin: auto;
  padding: 1%;
}
</style>