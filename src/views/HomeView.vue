<script setup>
import SquareDiv from '../components/SquareDiv.vue'
import { ref } from 'vue'

const isAnimationStopped = ref(false)
const isStopping = ref(false)

// const toggleAnimation = () => {
//   if (!isAnimationStopped.value) {
//     isStopping.value = true
//     setTimeout(() => {
//       isAnimationStopped.value = true
//       isStopping.value = false
//     }, 1000) // Adjust timing for smoother stop
//   } else {
//     isAnimationStopped.value = false
//   }
// }
</script>

<template>
  <main :class="{ 'stop-animation': isAnimationStopped, 'easing-out': isStopping }">
    <SquareDiv v-for="n in 240" :key="n" class="square" />
    <!-- <div class="overlay">
      <div class="overlay-content">
        <div class="overlay-content-top">
            <p class="contentTitle">Joel Rennert</p>
            <p class="contentSubtitle">High Functioning Creative Individual</p>

        
          <div class="overlay-content-top-right" @click="toggleAnimation"></div>
        </div>
        <div class="overlay-content-mid">
          <div class="contentContainerMid">
            <div class="cubeWrapper">
              
              <img class="cubeImage " src="../assets/bluebg.png" />
            </div>
          </div>
          <div class="contentContainerBottom">
            <p class="contentTextSmall">mywebsitejoel.com</p>
          </div>
        </div> 
      </div>
    </div> -->
  </main>
</template>

<style scoped>
@keyframes float {
  0% {
    transform: translate(0, 0) scale(1) rotate(0deg) skew(0deg);
    filter: drop-shadow(5px -5px 8px rgba(0, 0, 0, 0.3));
  }
  15% {
    transform: translate(-10px, -5px) scale(1.05) rotate(5deg) skew(2deg, 1deg);
    filter: drop-shadow(10px -10px 10px rgba(0, 0, 0, 0.2));
  }
  30% {
    transform: translate(10px, -10px) scale(0.92) rotate(-3deg) skew(-2deg, 1deg);
    filter: drop-shadow(
      15px -12px 12px rgba(0, 0, 0, 0.15)
    ); /* Strong upper-right when moving up-right */
  }
  50% {
    transform: translate(0px, 10px) scale(1.03) rotate(7deg) skew(3deg, -2deg);
    filter: drop-shadow(5px 5px 8px rgba(0, 0, 0, 0.25));
  }
  70% {
    transform: translate(-15px, 0px) scale(0.88) rotate(-4deg) skew(-3deg, 2deg);
    filter: drop-shadow(12px -5px 10px rgba(0, 0, 0, 0.2));
  }
  85% {
    transform: translate(10px, -5px) scale(1.05) rotate(2deg) skew(1deg, -1deg);
    filter: drop-shadow(10px -8px 10px rgba(0, 0, 0, 0.2));
  }
  100% {
    transform: translate(0, 0) scale(1) rotate(0deg) skew(0deg);
    filter: drop-shadow(5px -5px 8px rgba(0, 0, 0, 0.3));
  }
}

@keyframes easingBack {
  from {
    transform: none;
  }
  to {
    transform: translate(0, 0) scale(1) rotate(0deg) skew(0deg);
  }
}

.easing-out {
  animation: easingBack 1s forwards ease-out;
}

.stop-animation {
  animation-play-state: paused !important;
  animation-timing-function: ease-out !important;
}

.square {
  padding: 48px;
}

main {
  position: relative;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  width: 100vw;
  height: 100vh;
  background-color: #7f7d5572;
  gap: 10px;
  overflow-y: hidden;
  overflow-x: hidden;
  font-family: 'IBM Plex Mono';
  font-style: italic;
  color: #333;
  border-radius: 6px;
  /* animation: float 40s infinite;
  animation-timing-function: ease-in-out; */
  box-shadow:
    0 4px 12px rgba(0, 0, 0, 0.321),
    0 2px 4px rgba(0, 0, 0, 0.263);
}

main::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-image: url('../assets/lines.jpg');
  /* background-image: url('../assets/bluebg.png'); */
  background-size: cover;
  background-position: center;
  opacity: 0.3;
  z-index: -1;
}

.overlay {
  position: absolute;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  top: 15%;
  left: 10%;
  width: 100vw;
  height: 100vh;
  display: flex;
  justify-content: flex-start;
  align-items: flex-start;
  z-index: 2;
  gap: 5px;
}

.overlay-title {
  display: flex;
  justify-content: center;
  align-items: center;

  width: 60vw;
  height: 8vh;
  flex-wrap: wrap;
  color: #333;
  font-family: 'IBM Plex Mono';
  font-size: 1rem;
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 16px;
  backdrop-filter: blur(10px) saturate(180%);
  -webkit-backdrop-filter: blur(10px) saturate(180%);
  background-color: rgba(255, 255, 255, 0.128);
  box-shadow:
    0 4px 12px rgba(0, 0, 0, 0.15),
    0 2px 4px rgba(0, 0, 0, 0.1);
  z-index: 2;
  margin-left: 10%;
}

.overlay-content {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: flex-start;
  width: 80vw;
  height: 100%;
  flex-wrap: wrap;
  padding: 10px;
  color: #4e5246;
  font-family: 'IBM Plex Mono';
  font-size: 1rem;
  border: 1px solid #9da68f;
  border-radius: 8px;
  box-shadow: 0 4px 30px rgba(0, 0, 0, 0.163);
  z-index: 2;
  padding: 20px;
  background-color: transparent;
  opacity: 0.9;
  transition:
    background-color 0.1s ease,
    transform 0.1s ease,
    box-shadow 0.3s ease;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
}

.overlay-content:hover {
  transform: scale(0.98);
  box-shadow: 0 12px 40px rgba(0, 0, 0, 0.25);
  cursor: pointer;
}

.overlay-content-top {
  font-size: 1rem;
  color: 333;
  font-style: none;
  color: #424242;
  display: flex;
  text-shadow: none;
  font-weight: 400;

  letter-spacing: 0px;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 10%;
  flex-grow: 1;
  padding: 20px;
  background-color: rgba(0, 0, 0, 0.145);

  border-top-left-radius: 16px;
  border-top-right-radius: 16px;
  text-shadow: 7px 8px 8px rgba(59, 2, 2, 0.094);
  background-color: rgba(116, 116, 116, 0.099);
  background-color: rgba(116, 116, 116, 0.222);
  text-shadow: 2px 2px 2px rgba(0, 0, 0, 0.138);
}

.overlay-content-top-right {
  display: flex;
  justify-content: right;
  flex-grow: 1;
  width: 70%;
  overflow: hidden;
  padding: 5px;
  cursor: pointer;
}
@keyframes outsideBounce {
  0% {
    transform: translateX(-100%);
  }
  50% {
    transform: translateX(10%);
  }
  100% {
    transform: translateX(-100%);
  }
}

.overlay-content-top-right::after {
  content: '🍄';
  display: inline-block;
  animation: outsideBounce 4s linear infinite;
  white-space: nowrap;
}
.stop-animation {
  animation-play-state: paused !important;
}

.overlay-content-mid {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: left;
  width: 100%;
  height: 90%;
  padding: 20px;
  gap: 20px;

  background-color: rgba(116, 116, 116, 0.099);
  border-bottom-left-radius: 16px;
  border-bottom-right-radius: 16px;
  box-shadow:
    0 4px 12px rgba(0, 0, 0, 0.15),
    0 2px 4px rgba(0, 0, 0, 0.1);
}

.cubeWrapper {
  display: flex;
  justify-content: flex-end;
  align-items: flex-end;
  width: 100%;
  height: 100%;
  margin-top: 100px;
}

.cubeImage {
  width: 100%;
  height: 120%;
  /* animation: float 120s infinite;
  animation-timing-function: ease-in-out; */
  border-radius: 20px;
  filter: drop-shadow(5px -5px 8px rgba(0, 0, 0, 0.3));
  mix-blend-mode: multiply;
}

.contentText {
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 1.2rem;
  line-height: 1.2;
  letter-spacing: -1px;
  font-weight: 300;
}

.contentTitleAndSubtitle {
  display: flex;
}

.contentContainerMid {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 20px;
  gap: 10px;
  height: 80%;
}
.contentContainerBottom {
  display: flex;
  justify-content: flex-end;
  width: 100%;
}

.contentTitle {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 40%;
  font-size: 1.5rem;
  line-height: 1.2;
  letter-spacing: -1px;
  font-weight: 300;
  flex-grow: 5;
}
.contentSubtitle {
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 1rem;
  width: 100%;
  flex-grow: 1;
  line-height: 1.2;
  letter-spacing: -1px;
  font-weight: 300;
}

.contentTextSmall {
  display: flex;
  width: 100%;
  height: 10%;
  justify-content: right;
  align-items: flex-end;
  font-size: 1rem;
  font-weight: 300;
  line-height: 1.2;
  text-align: right;
}
</style>
