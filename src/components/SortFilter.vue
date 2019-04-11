<template>
  <div>
    <div class="sort">
      sort by :
      <a
        v-for="(type, index) of sortTypes"
        v-text="type"
        @click="sort(type)"
        :key="index"
        :class="{'is_sorted': isSorted(type)}"
        class="sort-item"
        href="javascript:void(0);"
      ></a>
    </div>
    <div class="filter">
      <label><input @click="filter($event)" type="checkbox">check my favorite movies</label>
    </div>
  </div>
</template>

<script>
export default {
  name: 'SortFilter',
  props: ['sortTypes'],
  data () {
    return {
      presentSortType: null
    }
  },
  methods: {
    sort (type) {
      this.presentSortType = type
      this.$emit('sort', type)
    },
    isSorted (type) {
      return this.presentSortType === type
    },
    filter (event) {
      this.$emit('filter', event.target.checked)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.sort, .filter {
  font-size: 1.2rem;
  padding: 10px;
  text-align: left;
}
.sort-item {
  display: inline-block;
  padding: 0 5px;
  text-decoration: none;
}
.sort-item.is_sorted {
  color: #2e963d;
  font-weight: bold;
}
.sort-item:not(:last-child):after {
  content: '|';
  color: #ccc;
  font-weight: normal;
  margin-left: 10px;
}
</style>
