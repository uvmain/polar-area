<script setup>
import html2canvas from 'html2canvas'

async function downloadImage() {
  const captureDiv = document.getElementById('capture-div')

  try {
    const canvas = await html2canvas(captureDiv)
    const dataURL = canvas.toDataURL('image/png')

    const a = document.createElement('a')
    a.href = dataURL
    a.download = 'captured-image.png'
    a.style.display = 'none'
    document.body.appendChild(a)

    a.click()

    document.body.removeChild(a)
  } catch (error) {
    console.error('Error capturing the image:', error)
  }
}
</script>

<template>
  <div>
    <button @click="downloadImage">Download Image</button>
  </div>
</template>

<style scoped>
button {
  color: black;
  background-color:white;
}
</style>