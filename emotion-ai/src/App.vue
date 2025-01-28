<template>
  <div class="min-h-screen bg-gray-100 flex items-center justify-center">
    <div class="bg-white p-6 rounded shadow-md w-full max-w-md">
      <h1 class="text-xl font-bold mb-4">Audio to Video Converter</h1>
      <form @submit.prevent="processAudio" class="space-y-4">
        <!-- File Input -->
        <div>
          <label class="block mb-2 text-sm font-medium text-gray-700">
            Upload Audio File
          </label>
          <input
            type="file"
            @change="handleFileChange"
            accept="audio/*"
            class="border rounded p-2 w-full"
          />
        </div>
        <!-- Process Button -->
        <button
          type="submit"
          :disabled="!audioFile"
          class="w-full bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded"
        >
          Process
        </button>
      </form>
      <!-- Download Section -->
      <div v-if="videoUrl" class="mt-4">
        <a
          :href="videoUrl"
          download="output-video.mp4"
          class="bg-green-500 hover:bg-green-700 text-white font-bold py-2 px-4 rounded block text-center"
        >
          Download Video
        </a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      audioFile: null, // The uploaded audio file
      videoUrl: null,  // URL to download the generated video
    };
  },
  methods: {
    handleFileChange(event) {
      this.audioFile = event.target.files[0];
    },
    async processAudio() {
      if (!this.audioFile) return;

      try {
        // Simulate file processing or send it to your backend
        console.log("Processing:", this.audioFile);

        // For now, create a mock URL (replace with actual backend logic)
        this.videoUrl = URL.createObjectURL(this.audioFile); // Replace with backend response
      } catch (error) {
        console.error("Error processing audio:", error);
      }
    },
  },
};
</script>

<style>
body {
  font-family: Arial, sans-serif;
}
</style>
