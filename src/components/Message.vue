<template>
  <div class="row message" v-bind:class="{ read: email.read, unread: !email.read, selected: email.selected}">
    <div class="col-xs-1">
      <div class="row">
        <div class="col-xs-2">
          <input v-on:click='toggle(email)' class='check' type="checkbox" v-model="checked"/>
        </div>
        <div v-on:click="starred(email)" class="col-xs-2">
          <icon v-if='email.starred' class="star" name='star'></icon>
          <icon v-if='!email.starred' class="star" name='star-o'></icon>
        </div>
      </div>
    </div>
    <div class="col-xs-11 body">
      <a href="#">
        <b-badge class='label label-warning' variant="warning" v-for='label in email.labels' key=''>{{label}}</b-badge>
        {{email.subject}}
      </a>
    </div>
  </div>
</template>

<script>
export default {
  name: 'email',
  props: ['email', 'toggle', 'starred'],
  data() {
    return {
      checked: this.email.selected
    }
  },

  methods: {

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
