<template>
    <!-- Modal -->
<div class="modal fade" id="mapDialog" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
  <div class="modal-dialog" role="document">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="exampleModalLabel">Modal title</h5>
        <button type="button" class="close" data-dismiss="modal" aria-label="Close">
          <span aria-hidden="true">&times;</span>
        </button>
      </div>
      <div class="modal-body">
        ...
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
        <button type="button" class="btn btn-primary">Save changes</button>
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

        },
        methods: {
            openDialog: function(){
                $('#mapDialog').modal('show');
            }
        }
    }
</script>