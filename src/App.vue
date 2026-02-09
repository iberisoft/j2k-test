<script setup>
import { ref, onMounted } from 'vue'
import * as cornerstone from 'cornerstone-core'
import * as cornerstoneWadoImageLoader from 'cornerstone-wado-image-loader'
import * as dicomParser from 'dicom-parser'

cornerstoneWadoImageLoader.external.cornerstone = cornerstone;
cornerstoneWadoImageLoader.external.dicomParser = dicomParser;

const image = ref(null);

onMounted(async () => {
  image.value = await cornerstone.loadAndCacheImage('wadouri:good-image.dcm');
});
</script>

<template>
  <div id="app">
    <h1 v-if="image">Image loaded: {{image.width}} x {{image.height}} pixels</h1>
  </div>
</template>
