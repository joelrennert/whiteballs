<template>
  <div class="square"><a href="#"></a></div>
</template>

<script>
export default {
  data() {
    return {
      
    }
  },
}
</script>

<style scoped>
img {
  width: 10vw;
  height: 10vh;
}


.square {
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 3.4rem;
  padding: 60px;
  animation: spin 8s linear infinite;
  border-radius: 50%;

  box-shadow: 
    10px 10px 20px rgba(64, 67, 60, 0.347),    
    -10px -10px 20px rgba(218, 215, 191, 0.802),
    inset 8px 8px 15px rgba(64, 67, 60, 0.4),    
    inset -8px -8px 15px rgba(255, 255, 255, 0.736); 

  background: radial-gradient(circle, 
    rgb(255, 255, 255) 0%,   
    rgba(193, 193, 193, 1) 100%
  );
}

.square:nth-child(even) {
  animation: spinReverse 7s linear infinite;
}

@keyframes spin {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(359deg);
  }
}

@keyframes spinReverse {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(-359deg);
  }
}
</style>
