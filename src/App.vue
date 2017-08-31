<template>
  <div id="app">
    <toolbar :minus='minus' :check='check' :blank='blank' :showCompose='showCompose' :show='show'></toolbar>
    <compose v-show='show'></compose>
    <messages :emails='emails' :toggle='toggle' :starred='starred'></messages>
  </div>
</template>

<script>
import Toolbar from './components/Toolbar'
import Messages from './components/Messages'
import Compose from './components/Compose'
import Data from './Data/seeds'

export default {
  name: 'app',
  components: {
    Toolbar,
    Messages,
    Compose
  },
  data() {
    return{
      show: false,
      emails: Data,
      minus: false,
      check: false,
      blank: true,
    }
  },
  methods: {
    toggle(message) {
      message.selected = !message.selected
    },
    bulkSelect() {

    },
    showCompose() {
      if (this.$data.show === true) {
        this.$data.show = false
      }
      else {
        this.$data.show = true
      }
    },
    starred(message) {
      message.starred = !message.starred
    },
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  margin-left: 1.5em;
  color: #2c3e50;
  margin-top: 60px;
}

.toolbar {
  margin-top: 1em;
  margin-bottom: 1em;
}

.toolbar .label-select {
  width: auto;
  display: inline;
}

.toolbar select,
.toolbar button,
.toolbar a,
.toolbar .badge {
  margin-right: .5em;
  margin-bottom: .5em;
}

.message {
  margin-left: 0px;
  padding-top: 8px;
  padding-bottom: 8px;
  cursor: pointer;
  border-bottom: 1px solid #efefef;
}

.message a {
  color: black;
}

.message a:hover, .message a:active, .message a:focus {
  text-decoration: none;
}

.message + .message {
  border-top: 1px solid #efefef;
}

.message.read {
  background: #efefef;
}

.message.unread {
  font-weight: bold;
}

.message.selected {
  background: #ffffcc;
}

.message:hover {
  margin-left: -3px;
  border-left: 3px solid #ccc;
}

.message-body {
  background: #ccc;
  margin-left: 0;
  margin-bottom: 1em;
  padding-top: 1em;
  padding-bottom: 1em;
}

.check {
  margin-left: 2em;
}

.star {
  margin-left: 1em;
  margin-right: 4em;
}

.pull-right {
  display: inline-block;
  margin-left: 20%;
}

footer.spacer {
  margin-bottom: 20em;
}

.label {
  margin-right: .5em;
}

.fa-close {
  cursor: pointer;
}
</style>
