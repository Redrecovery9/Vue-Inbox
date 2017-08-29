<template>
  <div class="messages">
    <div class="row message unread">
      <div class="col-xs-1">
        <div class="row">
          <div class="col-xs-2">
            <input type="checkbox" />
          </div>
          <div class="col-xs-2">
            <icon class="star" name="star-o"></icon>
          </div>
        </div>
      </div>
      <div class="col-xs-11">
        <a href="#">
          Here is some message text that has a bunch of stuff
        </a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'messages',
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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
