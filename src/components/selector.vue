<script setup>
import { ref } from "vue";
import axios from "axios";

const data = ref(null);
const movieid = ref("1");

const getMovie = async () => {
  movieid.value = (
    await axios.get("http://api.themoviedb.org/3/search/movie", {
      params: {
        api_key: "d2efec38e7d74d12122672897f241cbf",
        include_adult: "false",
        query: data,
      },
    })
  ).data.results;
  console.log(movieid.value);
}

// const getTrailer = async () => {
//     await axios.get("https://api.themoviedb.org/3/search/movie", {
//       params: {
//         api_key: "d2efec38e7d74d12122672897f241cbf",
//         append_to_response: "videos",
//       }}).then((response) => {
//         const trailers = movieData.data.videos.results.filter((trailer) => trailer.type === "Trailer");
//       });
// }
</script>

<template>
<div id="searchBox">
    <form action="index.html" method="get" @submit.prevent="getMovie">
        <select name="select" id="movie" class="select" v-model = "data">
          <option value="None">None</option>
          <option value="EL CAMINO">EL CAMINO</option>
          <option value="Parasite">Parasite</option>
          <option value="Green Book">Green Book</option>
          <option value="The Shape of Water">The Shape of Water</option>
          <option value="Moonlight">Moonlight</option>
          <option value="The King's Speech">The King's Speech</option>
          <option value="The Hurt Locker">The Hurt Locker</option>
          <option value="Chicago">Chicago</option>
          <option value="Argo">Argo</option>
          <option value="American Beauty">American Beauty</option>
        </select>
      <button class="button" type="submit" id="get" @click="getMovie">Get</button>
    </form>
</div>
    <div v-for="movie in movieid" v-if="movieid">
      <p class="movieData">
        <br> Title: {{movie.title}}
        <br> Release Date: {{movie.release_date}} &nbsp; : {{movie.popularity}}
        <br> Language: {{movie.origin_language}} &nbsp; Vote: {{movie.vote_count}} &nbsp; Vote Average: {{movie.vote_average}}
        <br> Violence: {{movie.adult}} &nbsp; Intensive Language: {{movie.adult}}
      </p>
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
  margin-top: 700px;
  float: left;
  height: 60px;
  width: 200px;
  text-align: center;
  font-size: 25px;
  border-radius: 10px;
  border-width: 2px;
  font-family: Georgia, 'Times New Roman', Times, serif;
}

.button{
  margin-top: 700px;
  float: left;
  height: 60px;
  width: 60px;
  border-radius: 10px;
  font-size: 25px;
}

p {
  margin-top: 100px;
  color: white;
  font-weight: bolder;
  font-family: 'Courier New', Courier, monospace;
  font-size: larger;
  background-color: gray;
  border-radius: 20px;
  width: 950px;
  text-align: center;
}
</style>