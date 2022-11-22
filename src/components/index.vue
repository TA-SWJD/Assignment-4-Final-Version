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
</template>

<script setup>
import { ref } from "vue";
</script>

<style scoped>
button {
  background-color: black;
  color: white;
  border-radius: 10px;
}

button:hover{
  background-color:white;
  color: black;
}

.select{
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