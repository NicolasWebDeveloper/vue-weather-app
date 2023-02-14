<template>
  <teleport to="body">
    <div>
      <div class="spinner"></div>
    </div>
  </teleport>
</template>

<style scoped>
div {
  position: fixed;
  height: 100vh;
  width: 100vw;
  background-color: #0000007c;
  display: flex;
  justify-content: center;
  align-items: center;
}

.spinner {
  height: 10rem;
  width: 10rem;
  border-radius: 50%;
  border: 20px solid black;
  border-color: #00000095 #00000095 white white;
  background-color: transparent;
  animation: rotate-spinner 1.2s linear infinite;
}

@keyframes rotate-spinner {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
</style>
