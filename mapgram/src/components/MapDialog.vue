<template>
    <!-- Modal -->
<div class="modal fade" id="mapDialog" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
  <div class="modal-dialog" role="document">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="exampleModalLabel">{{title}}</h5>
        <button type="button" class="close" data-dismiss="modal" aria-label="Close">
          <span aria-hidden="true">&times;</span>
        </button>
      </div>
      <div class="modal-body">
          <img src="https://placehold.jp/150x150.png" class="img-rounded img-responsive">
          <img v-if="!isNotUploadImage" :src="uploadImageUrl" />
          <br/>
          <v-file-input placeholder="Upload your photo" label="Photo input" @change="onImagePicked"></v-file-input>      
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-dismiss="modal" v-on:click="clearImage">Close</button>
        <button type="button" class="btn btn-primary" v-bind:disabled="!uploadImageUrl" v-on:click="uploadImage">Upload</button>
        <!-- <label><span type="button" class="btn btn-primary">Add Photo<input type="file" style="display:none"></span></label> -->
      </div>
    </div>
  </div>
</div>
</template>
<script src="https://code.jquery.com/jquery-3.3.1.js"></script>
<script>
    export default {
        name: 'MapDialog',
        data: () => {
            return {
                title:"",
                uploadImageUrl:"",
                isNotUploadImage: true
            }
        },
        computed: {
        },
        methods: {
            openDialog: function(reg){
                this.title = reg;
                $('#mapDialog').modal('show');
            },
            onImagePicked: function(file) {
                if (file !== undefined && file !== null) {
                    if (file.name.lastIndexOf('.') <= 0) {
                    return
                    }
                    const fr = new FileReader()
                    fr.readAsDataURL(file)
                    fr.addEventListener('load', () => {
                    this.uploadImageUrl = fr.result
                    })
                } else {
                    console.log("キャンセル");
                    this.uploadImageUrl = ''
                    this.isNotUploadImage = true;
            }
            },
            uploadImage: function() {
              this.isNotUploadImage = false;
            },
            clearImage: function() {
              this.uploadImageUrl = '' 
            }
        }
    }
</script>