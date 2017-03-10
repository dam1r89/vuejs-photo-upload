<template>
  <div class="photo-upload">
    <div class="uploader" :class="{hovering: hovering}" :style="{backgroundImage: backgroundImage}" ref="uploader">
      <span v-show="!(value || preview)" class="upload-instructions">
        Click or drag
        <br>
        here image
        <br>
        for upload
      </span>
      <input class="file-photo" type="file" @change="handleImage" @dragenter="hovering = true"
             @dragleave="hovering = false"/>
    </div>
  </div>
</template>

<style>
  .uploader {
    position: relative;
    overflow: hidden;
    width: 300px;
    height: 250px;
    background-color: #f3f3f3;
    background-size: contain;
    background-position: center center;
    background-repeat: no-repeat;
    border: 2px dashed #e8e8e8;
  }

  .uploader.hovering {
    background-color: #bbb;
  }

  .uploader:hover {
    background-color: skyblue;
  }

  .upload-instructions {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translateX(-50%) translateY(-50%);
    text-align: center;
  }

  .file-photo {
    position: absolute;
    width: 300px;
    height: 400px;
    top: -50px;
    left: 0;
    z-index: 2;
    opacity: 0;
    cursor: pointer;
  }

  .uploader img {
    position: absolute;
    width: 100%;
    top: -1px;
    left: -1px;
    z-index: 1;
    border: none;
  }

</style>

<script>

    export default {
        props: ['value'],
        methods: {
            handleImage(event) {

                let files = event.target.files;
                let reader = new FileReader();
                reader.onload = (event) => {
                    this.preview = event.target.result;
                    this.$emit('input', files[0]);
                };
                reader.readAsDataURL(files[0]);

            }
        },
        data() {
            return {
                hovering: false,
                preview: null
            }
        },
        computed: {
            backgroundImage() {
                let image = this.preview || this.value;
                if (!image) {
                    return null;
                }
                return `url('${image}')`;
            }
        }
    }
    
</script>
