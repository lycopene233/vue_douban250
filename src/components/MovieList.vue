<template>
  <div>
    <div
      is="sort-filter"
      :sortTypes="sortTypes"
      @sort="handleSort"
      @filter="handleFilter"
    ></div>
    <ul class="movie-list">
      <li
        is="movie-item"
        v-for="(movie, index) of movieList"
        :key="index"
        :movie="movie"
        :isFiltered="isFiltered"
      ></li>
    </ul>
    <p class="msg" v-show="isLoading" v-text="text.loadingMsg"></p>
    <p v-show="canGetMoreMovie" class="msg" v-text="text.scrollMsg"></p>
  </div>
</template>

<script>
import MovieItem from './MovieItem'
import SortFilter from './SortFilter'

export default {
  name: 'MovieList',
  data () {
    return {
      doubanApi: {
        url: 'https://api.douban.com/v2/movie/top250',
        start: 0,
        count: 30,
        total: 250
      },
      movieList: [],
      sortTypes: ['newest', 'oldest', 'rating'],
      text: {
        loadingMsg: 'loading...',
        scrollMsg: 'scroll down to see more'
      },
      isLoading: false,
      isFiltered: false
    }
  },
  components: {
    'movie-item': MovieItem,
    'sort-filter': SortFilter
  },
  mounted () {
    this.getMovieData()
    window.addEventListener('scroll', this.handleScroll)
  },
  computed: {
    apiUrl () {
      return `${this.doubanApi.url}?start=${this.doubanApi.start}&count=${this.doubanApi.count}`
    },
    canGetMoreMovie () {
      let count = this.movieList.length
      return (!this.isLoading && !this.isFiltered && count > 0 && count < this.doubanApi.total)
    }
  },
  methods: {
    getMovieData () {
      if (this.isLoading) return

      this.isLoading = true
      console.log('start getting data...')

      this.$http.jsonp(this.apiUrl)
        .then((res) => {
          this.isLoading = false
          this.movieList = [...this.movieList, ...res.body.subjects]
          this.doubanApi.start += this.doubanApi.count
        }, (err) => {
          console.log(err)
          this.loadingMsg = 'fail to load data from douban'
        })
    },
    handleScroll () {
      if (!this.canGetMoreMovie) return
      if (window.scrollY + window.screen.availHeight >= document.body.clientHeight) {
        this.getMovieData()
        this.isLoading = true
      }
    },
    handleSort (type) {
      switch (type) {
        case 'newest':
          this.movieList.sort((a, b) => (b.year - a.year))
          break
        case 'oldest':
          this.movieList.sort((a, b) => (a.year - b.year))
          break
        case 'rating':
          this.movieList.sort((a, b) => (b.rating.average - a.rating.average))
          break
      }
    },
    handleFilter (checked) {
      this.isFiltered = checked
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.movie-list {
  padding: 10px 5px;
}
.msg {
  margin: 20px 0;
}
</style>
