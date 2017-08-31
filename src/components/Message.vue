<template>
  <div class="row message" v-bind:class="{ read: email.read, unread: !email.read, selected: email.selected}">
    <div class="col-xs-1">
      <div class="row">
        <div class="col-xs-2">
          <input v-on:click='toggle(email)' class='check' type="checkbox" v-model="checked"/>
        </div>
        <div v-on:click="starred" class="col-xs-2">
          <icon v-if='email.starred' class="star" v-bind:name='star'></icon>
          <icon v-if='!email.starred' class="star" v-bind:name='staro'></icon>
          <!-- <icon class="star" v-bind:name='myIcon'></icon> -->
        </div>
      </div>
    </div>
    <div class="col-xs-11">
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
  props: ['email', 'toggle'],
  data() {
    return {
      staro: 'star-o',
      star: 'star',
      checked: this.email.selected
    }
  },

  methods: {
    starred: function() {
      let data = this.$data;
      // data.staro = 'star'
      // data.star = 'star-o'

      if (data.staro === 'star-o') {
        data.staro = 'star'
      }
      else if (data.star === 'star') {
        data.star = 'star-o'
      }
      else {
        data.staro = 'star-o'
        data.star = 'star'
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
