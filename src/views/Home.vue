<template>
  <div class="home">
    <input type="file" name="file-to-upload" class="inputFile" ref="files" @change="uploadFile" />
    <!-- name="file-to-upload"
    enctype="multipart/formdata"-->
  </div>
</template>

<script>
// @ is an alias to /src
export default {
  name: "Home",
  methods: {
    uploadFile() {
      const uploadFile = this.$refs.files.files[0];
      const formData = new FormData();
      formData.append("file-to-upload", formData);
      console.log(formData);

      this.$http
        .post("http://127.0.0.1:3000/uploadFile", formData, {
          headers: {
            "Content-type": "multipart/formdata"
          }
        })
        .then(res => {
          console.log(res);
        });
    }
  }
};
</script>
