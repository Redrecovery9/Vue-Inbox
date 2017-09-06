<template>
  <div id="app">
    <toolbar :showCompose='showCompose'
    :show='show' :bulkSelect='bulkSelect' :bulkCheckbox='bulkCheckbox'
    :halfCheckbox='halfCheckbox' :emptyCheckbox='emptyCheckbox'
    :unreadCount='unreadCount' :markRead='markRead' :markUnread='markUnread'
    :emails='emails' :selected='selected' :options='options'
    :unselected='unselected' :unoption='unoption' :deleteSelected='deleteSelected'></toolbar>
    <compose v-show='show'></compose>
    <messages :emails='emails' :starred='starred'></messages>
  </div>
</template>

<script>
import Toolbar from './components/Toolbar'
import Messages from './components/Messages'
import Compose from './components/Compose'
const baseURL = 'https://calm-dawn-17844.herokuapp.com/api'

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
      emails: [],
      selected: null,
      options: [
        {value:null, text: 'Apply Label'},
        {value:'dev', text: 'dev'},
        {value:'personal', text: 'personal'},
        {value:'gschool', text: 'gschool'},
      ],
      unselected: null,
      unoption: [
        {value:null, text: 'Remove Label'},
        {value:'dev', text: 'dev'},
        {value:'personal', text: 'personal'},
        {value:'gschool', text: 'gschool'},
      ]
    }
  },
  async mounted(){
    const data = await fetch(`${baseURL}/messages`)
    const response = await data.json()
    this.emails = response._embedded.messages.map(message => {
      message.selected = false
      return message
    })
  },
  computed: {
    unreadCount() {
      return this.emails.reduce((acc, email) => {
        if (email.read == false) {
          acc++
        }
        return acc
      }, 0)
    },
    bulkCheckbox() {
      return this.emails.every(email => email.selected)
    },
    halfCheckbox() {
      return this.emails.some(email => email.selected) && !this.bulkCheckbox
    },
    emptyCheckbox() {
      return this.emails.every(email => !email.selected)
    }
  },
  methods: {
    bulkSelect() {
      if (this.bulkCheckbox) {
        this.emails.forEach(email => this.$set(email, 'selected', false))
      } else {
        this.emails.forEach(email => this.$set(email, 'selected', true))
      }
    },
    showCompose() {
      if (this.$data.show === true) {
        this.$data.show = false
      }
      else {
        this.$data.show = true
      }
    },
    starred(email) {
      email.starred = !email.starred
      const data = {
        "messageIds": [email.id],
        "command": "star",
        "star": email.starred
      }
      const settings = {
        method: 'PATCH',
        headers: {
          'content-type': 'application/json'
        },
        body: JSON.stringify(data)
      };
      fetch(`${baseURL}/messages`, settings)
       .then(response => {
         if(response.ok){
           console.log(response);
         }
       })
    },
    markRead() {
      const ids = []
      for (let i = 0; i < this.emails.length; i++) {
        if (this.emails[i].selected) {
          this.emails[i].read = true
          ids.push(Number(this.emails[i].id))
        }
      }
      const data = {
        "messageIds" : ids,
        "command" : "read",
        "read" : true
      };
      const settings = {
        method: 'PATCH',
        headers: {
          'content-type': 'application/json'
        },
        body: JSON.stringify(data)
      };
      fetch(`${baseURL}/messages`, settings)
       .then(response => {
         if(response.ok){
           console.log(response);
         }
       })
    },
    markUnread() {
      const ids = []
      for (let i = 0; i < this.emails.length; i++) {
        if (this.emails[i].selected) {
          this.emails[i].read = false
          ids.push(Number(this.emails[i].id))
        }
      }
      const data = {
        "messageIds" : ids,
        "command" : "read",
        "read" : false
      };
      const settings = {
        method: 'PATCH',
        headers: {
          'content-type': 'application/json'
        },
        body: JSON.stringify(data)
      };
      fetch(`${baseURL}/messages`, settings)
       .then(response => {
         if(response.ok){
           console.log(response);
         }
       })
    },
    deleteSelected(email) {

    }
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
  margin-right: .5em;
}

.star {
  margin-left: 1em;
  margin-right: 4em;
}

.body{
  margin-left: 1em;
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
