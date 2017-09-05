<template>
  <div class="row toolbar">
    <div class="col-md-12">

      <a class="btn btn-danger" v-on:click='showCompose'>
        <icon name="plus"></icon>
      </a>

      <b-button class="btn btn-default" v-on:click='bulkSelect()'>
        <icon v-if='halfCheckbox' name="minus-square-o"></icon>
        <icon v-if='emptyCheckbox' name="square-o"></icon>
        <icon v-if='bulkCheckbox' name="check-square-o"></icon>
      </b-button>

      <b-button class="btn btn-default" :disabled='emptyCheckbox'>Mark As Read</b-button>

      <b-button class="btn btn-default" :disabled='emptyCheckbox'>Mark As Unread</b-button>

      <select class="form-control label-select" :disabled='emptyCheckbox'>
        <option>Apply label</option>
        <option value="dev">dev</option>
        <option value="personal">personal</option>
        <option value="gschool">gschool</option>
      </select>

      <select class="form-control label-select" :disabled='emptyCheckbox'>
        <option>Remove label</option>
        <option value="dev">dev</option>
        <option value="personal">personal</option>
        <option value="gschool">gschool</option>
      </select>

      <b-button class="btn btn-default">
        <icon name="trash-o"></icon>
      </b-button>

      <p class="pull-right">
        <b-badge pill variant="" class='badge' name='badge'>{{ unreadCount }}</b-badge>
        unread messages
      </p>
    </div>
  </div>
</template>

<script>

export default {
  name: 'toolbar',
  props: ['bulkSelect', 'minus', 'check', 'blank', 'show', 'showCompose',
  'bulkCheckbox', 'halfCheckbox', 'emptyCheckbox', 'unreadCount'],
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
