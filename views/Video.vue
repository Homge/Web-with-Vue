<template>
    <div>
      <h1>Video</h1>
      <h1>Cute cat video</h1>
      <video controls class="w-full max-w-md mx-auto">
        <source src="~@/assets/hapi.mp4" type="video/mp4">
      </video>
    </div>
  </template>
  
  <script>
  export default {
    name: 'video'
  };
  </script>
  
  <style scoped>
  video {
    border-radius: 8px;
    margin-top: 1rem;
  }
  </style>