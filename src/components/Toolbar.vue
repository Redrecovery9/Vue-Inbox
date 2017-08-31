<template>
  <div class="row toolbar">
    <div class="col-md-12">

      <a class="btn btn-danger" v-on:click='showCompose'>
        <icon name="plus"></icon>
      </a>

      <b-button class="btn btn-default" v-on:click='bulkSelect'>
        <icon v-if='minus' name="minus-square-o"></icon>
        <icon v-if='blank' name="square-o"></icon>
        <icon v-if='check' name="check-square-o"></icon>
      </b-button>

      <b-button class="btn btn-default">Mark As Read</b-button>

      <b-button class="btn btn-default">Mark As Unread</b-button>

      <select class="form-control label-select">
        <option>Apply label</option>
        <option value="dev">dev</option>
        <option value="personal">personal</option>
        <option value="gschool">gschool</option>
      </select>

      <select class="form-control label-select">
        <option>Remove label</option>
        <option value="dev">dev</option>
        <option value="personal">personal</option>
        <option value="gschool">gschool</option>
      </select>

      <b-button class="btn btn-default">
        <icon name="trash-o"></icon>
      </b-button>

      <Badge></Badge>
    </div>
  </div>
</template>

<script>
import Badge from './Badge'

export default {
  name: 'toolbar',
  props: ['bulkSelect', 'minus', 'check', 'blank', 'show', 'showCompose'],
  components: {
    Badge
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
