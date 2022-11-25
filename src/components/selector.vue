<script setup>
import { ref } from "vue";
import axios from "axios";

const data = ref(null);
const movieid = ref(0);
let trailer = ref(null);

const getMovie = async () => {
  trailer = ref(null);
  movieid.value = (
    await axios.get("http://api.themoviedb.org/3/search/movie", {
      params: {
        api_key: "d2efec38e7d74d12122672897f241cbf",
        include_adult: "false",
        query: data.value,
      },
    })
  ).data.results[0];
  console.log(movieid.value);

  trailer.value =  (
    (
      await axios.get(`https://api.themoviedb.org/3/movie/${movieid.value.id}`, {
      params: {
        api_key: "d2efec38e7d74d12122672897f241cbf",
        append_to_response: "videos",
      }
    })
    ).data.videos.results.filter((trailer) => trailer.type === "Trailer").at(0).key);

    // (Playback error)
    // const getTrailer = async () => {
    // await axios.get("https://api.themoviedb.org/3/search/movie", {
    //   params: {
    //     api_key: "d2efec38e7d74d12122672897f241cbf",
    //     append_to_response: "videos",
    //   }}).then((response) => {
    //     const trailers = movieData.data.videos.results.filter((trailer) => trailer.type === "Trailer").at(0);
    //   });
    }

</script>

<template>
<div id="searchBox">
    <form action="index.html" method="get" @submit.prevent="getMovie">
        <select name="select" id="movie" class="select" v-model = "data" value = none>
          <option value="el-camino-a-breaking-bad-movie">EL CAMINO</option>
          <option value="The Dark Knight">The Dark Knight</option>
          <option value="Green Book">Green Book</option>
          <option value="The Shape of Water">The Shape of Water</option>
          <option value="Moonlight">Moonlight</option>
          <option value="The King's Speech">The King's Speech</option>
          <option value="The Hurt Locker">The Hurt Locker</option>
          <option value="Interstellar">Interstellar</option>
          <option value="Argo">Argo</option>
          <option value="Avatar">Avatar</option>
        </select>
      <button class="button" type="submit" id="get" @click="getMovie">Get</button>
    </form>
</div>
    <div v-if="movieid" >
      <p class="movieData">
        <br> Title: {{movieid.title}}
        <br> Release Date: {{movieid.release_date}} &nbsp; : {{movieid.popularity}}
        <br> Language: {{movieid.origin_language}} &nbsp; Vote: {{movieid.vote_count}} &nbsp; Vote Average: {{movieid.vote_average}}
        <br> Violence: {{movieid.adult}} &nbsp; Intensive Language: {{movieid.adult}}
        <br> Overview: {{movieid.overview}} <br>
        <br> ID: {{movieid.id}} &nbsp; Backdrop Path: {{movieid.backdrop_path}} <br>Poster Path: {{movieid.poster_path}}
        <br> .
      </p>
      <img v-if="movieid.poster_path" :src="'https://image.tmdb.org/t/p/w500' + movieid.poster_path" class="image">
      <iframe :src="'https://www.youtube.com/embed/' + trailer" class="Trailer"></iframe>
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
  margin-top: 100px;
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
  margin-top: 100px;
  float: right;
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

.Trailer {
  border-radius: 20px;
  height: 450px;
  aspect-ratio: 16 / 9;
}
.image {
  border-radius: 20px;
  height: 450px;
  aspect-ratio: 2/3;
}
</style>