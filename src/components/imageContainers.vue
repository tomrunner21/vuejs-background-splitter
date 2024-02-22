<template>
    <div class="container py-5">
      <header class="text-white text-center">
        <h1 class="display-4">Background Splitter:</h1>
      </header>

      <div class="row py-4">
        <div class="col-lg-6 mx-auto">
            <!-- Uploaded image area -->
            <p class="font-italic text-white text-center">The image uploaded will be rendered inside the box below.</p>
            <!-- Accesses function via button -->
            <input id="fileInput" type="file" @change="previewImage" accept="image/*">
            <!-- loads the uploaded image -->
            <div class="image-area mt-4" v-if="imageUrl">
                <img :src="imageUrl" alt="Preview" class="img-fluid rounded shadow-sm mx-auto d-block">
            </div>
      </div>
    </div>
    </div>
</template>

<script>
export default {
data() {
    return {
    imageUrl: null,
    };
},
methods: {
    previewImage(event) {
    const file = event.target.files[0];
    if (file && file.type.startsWith('image/')) {
        this.imageUrl = URL.createObjectURL(file);
    }
    }
}
};
</script>

<style>
#upload {
opacity: 0;
}
#upload-label {
position: absolute;
top: 50%;
left: 1rem;
transform: translateY(-50%);
}
.image-area {
/* border: 2px dashed rgba(255, 255, 255, 0.7); */
padding: 1rem;
position: relative;
}
.image-area::before {
/* content: 'Uploaded image result'; */
color: #fff;
font-weight: bold;
text-transform: uppercase;
position: absolute;
top: 50%;
left: 50%;
transform: translate(-50%, -50%);
font-size: 0.8rem;
z-index: 1;
}
.image-area img {
z-index: 2;
position: relative;
}
body {
min-height: 100vh;
background-color: #757f9a;
/* background-image: linear-gradient(147deg, #757f9a 0%, #d7dde8 100%); */
}
</style>
  
  