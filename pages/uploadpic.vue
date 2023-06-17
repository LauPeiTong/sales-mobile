<template>
  <div class="container">
    <input type="file" ref="fileInput" style="display: none" @change="handleFileUpload">
    <button class="upload-button" @click="openFileInput">Upload Invoice</button>
  </div>
</template>
<script>
export default {
  methods: {
    openFileInput () {
      this.$refs.fileInput.click()
    },
    handleFileUpload (event) {
      const file = event.target.files[0]
      // Perform any necessary processing or send the file to your software
      console.log('Uploaded file:', file)

      // Navigate to the assigned page
      this.$router.push('/home')
    }
  }
}
</script>

<style>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.upload-button {
  padding: 10px 20px;
  background-color: #4CAF50;
  color: white;
  border: none;
  border-radius: 4px;
  font-size: 16px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.upload-button:hover {
  background-color: #45a049;
}
</style>
