<template>
  <div class="toolbar">
    <div class="row toolbar">
      <div class="col-md-12">
        <p class="pull-right">
          <span class="badge badge">2</span>
          unread messages
        </p>

        <b-button class="btn btn-default">
          <icon name="check-square-o"></icon>
        </b-button>

        <b-button class="btn btn-default">
          Mark As Read
        </b-button>

        <b-button class="btn btn-default">
          Mark As Unread
        </b-button>

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
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'toolbar',
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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
