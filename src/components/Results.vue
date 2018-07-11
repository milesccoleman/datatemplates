<template>
  <div id="background">
  <div class="results">
    <h1 id="title">20 Movies You Should Watch</h1>
    <p class="search-meta">
      <span class="search"><b>Current Page:</b> {{page}}</span><br>
      <span class="search"><b>Pages:</b> {{total_pages}}</span><br>
      <span class="search"><b>Count:</b> {{total_results}}</span><br>
    </p>

    <ul id="card">
      <li class="movie-item" v-for="result in results">
        <img v-bind:src="'https://image.tmdb.org/t/p/w150_and_h225_bestv2'+result.poster_path" v-bind:alt="result.original_title + ' Poster'" class="poster-image">
        <h2 class="title"><a v-bind:href="'https://www.themoviedb.org/movie/'+result.id">{{result.title}}</a></h2>
        <div class="ratings">
          <span v-if="result.vote_average > 8" class="rating-category sure-bet">Super Popular</span>
          <span v-else-if="(result.vote_average >= 7.8)" class="rating-category might-be-worth-it">Very Popular</span>
          <span v-else-if="(result.vote_average >= 7.7)" class="rating-category a-gamble">Popular</span>
          <span v-else-if="(result.vote_average <= 7.6)" class="rating-category dont-waste-your-time">Good</span>
          <span class="vote-average">Rating: {{result.vote_average}}</span> - <span class="vote-count">{{result.vote_count}}</span> votes

        </div>
        <div class="trending">
          <span v-if="result.popularity >= 150" class="trending-category fire"><p>🔥 Trending</p></span>
        </div>
        <p class="overview">
          {{result.overview}}
        </p>
        <p class="release-date">Original Release: {{result.release_date}}</p>
        <ul class="genre-list">
          <li v-for="genre in result.genres">{{genre}}</li>
        </ul>
      </li>
    </ul>
  </div>
  </div>
</template>

<script>
import apiresults from '../apiresults.js'
export default {
  name: 'results',
  data () {
    return apiresults
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#background {
background: linear-gradient(270deg, #1fd27c, #13d4e8);
background-size: 400% 400%;

-webkit-animation: AnimationName 30s ease infinite;
animation: AnimationName 30s ease infinite;
}
@-webkit-keyframes AnimationName {
    0%{background-position:0% 67%}
    50%{background-position:100% 34%}
    100%{background-position:0% 67%}
}
@keyframes AnimationName {
    0%{background-position:0% 67%}
    50%{background-position:100% 34%}
    100%{background-position:0% 67%}
}
#card {
  background-color: white;
}
#title {
  text-align: center;
  font-size: 50px;
}
h1, h2 {
  margin: 0 0 1rem 0;
  color: white;
}

ul {
  list-style-type: none;
  padding: 0;
}
.search-meta {
  text-align: right;
}

.movie-item {
  margin: 10px 0;
  padding: 2rem;
  box-shadow: 4px 4px 10px rgba(270, #f0f50b, #82e60e,0.2);
}

.movie-item img {
  float: left;
  margin-right: 1rem;
}

.release-date {
  font-weight: 600;
  font-size: 12px;
  color: #333;
}

.results {
  background-color: rgba(0, 0, 0, 0);}

.rating-category {
  font-size: 12px;
  color: #fff;
  font-weight: 800;
  background: #ccc;
  padding: 0.5rem;
  border-radius: 4px;
}

.rating-category.sure-bet {
  background: #f46542;
}

.rating-category.might-be-worth-it {
  background: #cccc02;
}

.rating-category.a-gamble {
  background: #01c11e;
}

.rating-category.dont-waste-your-time {
  background: #02afce;
}

.search {
  color: white;
}

.trending {
  font-size: 12px;
  color: black;
  font-weight: 800;
  background: white;
  padding: 0.5rem;
  border-radius: 4px;
  font-size: 15px;
  float: right;

}

.genre-list li {
  border-radius: 4px;
  background: #666;
  color: #fff;
  font-weight: 800;
  font-size: 12px;
  padding: 0.5rem;
  display: inline-block;
  margin-right: 10px;
}

a {
  color: #42b983;
}
</style>
