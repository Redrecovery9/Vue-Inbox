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

      <b-button class="btn btn-default" :disabled='emptyCheckbox'
      v-on:click='markRead'>Mark As Read</b-button>

      <b-button class="btn btn-default" :disabled='emptyCheckbox'
      v-on:click='markUnread'>Mark As Unread</b-button>

      <b-form-select class="form-control label-select" v-model='selected'
      :options='options' :disabled='emptyCheckbox'>
        <div>Selected: <strong>{{ selected }}</strong></div></b-form-select>

      <b-form-select class="form-control label-select" v-model='unselected'
      :options='unoption' :disabled='emptyCheckbox'>
        <div>Selected2: <strong>{{ unselected }}</strong></div></b-form-select>

      <b-button class="btn btn-default" :disabled='emptyCheckbox'>
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
  props: ['bulkSelect', 'show', 'showCompose',
  'bulkCheckbox', 'halfCheckbox', 'emptyCheckbox', 'unreadCount',
  'markRead', 'markUnread', 'emails', 'selected', 'options',
  'unselected', 'unoption',],
  data(){
    return {

    }
  },
  watch: {
    selected: function(label) {
      if (label != null) {
        for (let i = 0; i < this.emails.length; i++) {
          let hasLabel = this.emails[i].labels.some(el => el == label)
          if (this.emails[i].selected && !hasLabel) {
            this.emails[i].labels.push(label)
          }
        }
      }
    },
    unselected: function(label) {
      if (label != null) {
        for (let i = 0; i < this.emails.length; i++) {
          let hasLabel = this.emails[i].labels.some(el => el == label)
          if (hasLabel && this.emails[i].selected) {
            let index = this.emails[i].labels.indexOf(label)
            this.emails[i].labels.splice(index, 1)
          }
        }
      }
    },
  },
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
