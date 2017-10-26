<template>
  <div class="compose">
    <form class="form-horizontal well">
      <div class="form-group">
        <div class="col-sm-8 col-sm-offset-2">
          <h4>Compose Message</h4>
        </div>
      </div>
      <div class="form-group">
        <label for="subject" class="col-sm-2 control-label">Subject</label>
        <div class="col-sm-8">
          <input type="text" class="form-control" id="subject" v-model='composEmail.subject' placeholder="Enter a subject" name="subject">
        </div>
      </div>
      <div class="form-group">
        <label for="body" class="col-sm-2 control-label">Body</label>
        <div class="col-sm-8">
          <textarea name="body" id="body" v-model='composEmail.message' class="form-control"></textarea>
        </div>
      </div>
      <div class="form-group">
        <div class="col-sm-8 col-sm-offset-2">
          <input v-on:click='compose' type="submit" value="Send" class="btn btn-primary">
        </div>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  props: ['show', 'compose', 'composEmail'],
  data() {
    return {

    }
  }
}
</script>

<style scoped>
</style>
