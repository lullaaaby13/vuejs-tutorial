<template>
  <div>
    <div class="row my-3" v-for="item in list" :key="item.seq">
      <div class="col-md-8 offset-md-2">
        <div class="card">
          <div class="card-body">
            <h5 class="card-title">{{ item.name }}</h5>
            <h6 class="card-subtitle mb-2 text-muted">{{ item.date }}</h6>
            <a
            href="#"
            class="btn btn-outline-success btn-sm mx-1">START</a>
            <a
            href="#"
            class="btn btn-outline-danger btn-sm mx-1">DELETE</a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    listName: String,
    list: Array,
    startAction: Function,
    deleteAction: Function,
  }
}
</script>
