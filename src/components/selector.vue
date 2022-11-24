<script setup>
import { ref } from "vue";
import axios from "axios";

const data = ref("");
const movieid = ref("1");

const getMovie = async () => {
  movieid.value = (
    await axios.get("http://api.themoviedb.rog/3/search/movie", {
      params: {
        api_key: "d2efec38e7d74d12122672897f241cbf",
        include_adult: "false",
        query: data.value,
      },
    })
  ).data.results;
};

const getTrailer = async (movie) => {
  movieid.value = (
    await axios.get("https://api.themoviedb.org/3/search/movie", {
      params: {
        api_key: "d2efec38e7d74d12122672897f241cbf",
        append_to_response: "videos",
      }}).then((response) => {
        const trailers = movieData.data.videos.results.filter((trailer) => trailer.type === "Trailer");
      }));
}
</script>

<template>
<div id="searchBox">
    <form action="index.html" method="get">
        <select name="select" id="movie" class="select">
          <option value="None">None</option>
          <option value="The Lord of the Rings">The Lord of the Rings</option>
          <option value="Harry Potter">Harry Potter</option>
          <option value="Resident Evil">Resident Evil</option>
          <option value="Breaking Bad">Breaking Bad</option>
          <option value="Spiderman">Spiderman</option>
          <option value="Star Wars">Star Wars</option>
          <option value="The Avengers">The Avengers</option>
          <option value="The Godfather">The Godfather</option>
          <option value="Terminator">Terminator</option>
          <option value="Alien">Alien</option>
        </select>
      <button class="button" type="submit" id="get">Get</button>
    </form>
    </div>
    <div v-for="movie in movieid" v-if="movieid">
      <p class="movieData">
        <br> Title: {{movie.title}}
        <br> Release Date: {{movie.release_date}} &nbsp; : {{movie.popularity}}
        <br> Language: {{movie.origin_language}} &nbsp; Vote: {{movie.vote_count}} &nbsp; Vote Average: {{movie.vote_average}}
        <br> Violence: {{movie.adult}} &nbsp; Intensive Language: {{movie.adult}}
      </p>
      <iframe src="'https://www.youtube.com/embed/' + trailers.at(0).key" frameborder="0"></iframe>
      <img v-if="movie.poster_path" src="'http://image.tmdb.org/t/p/w500' + movie.poster_path" alt="Poster" class="image">
    </div>
</template>

<style scoped>
button {
  margin-top: 90px;
  background-color: black;
  color: white;
  border-radius: 10px;
}

button:hover{
  background-color:white;
  color: black;
}

.select{
  margin-top: 90px;
  float: right;
  height: 60px;
  width: 200px;
  text-align: center;
  font-size: 25px;
  border-radius: 10px;
  border-width: 2px;
  font-family: Georgia, 'Times New Roman', Times, serif;
}

.button{
  float: right;
  height: 60px;
  width: 60px;
  border-radius: 10px;
  font-size: 25px;
}
</style>