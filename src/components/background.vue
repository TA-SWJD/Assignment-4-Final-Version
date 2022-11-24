<template>
    <div class="background">
      <img src="../assets/images/TMDB.png" alt="background" id="background">
    <div id="cover">
      <img src="https://hips.hearstapps.com/hmg-prod/images/lordoftherings-1636391090.jpg?crop=0.5xw:1xh;center,top&resize=640:*" alt="The Lord of the Rings" width="25%" id="p1">
      <img src="https://12ax7web.s3.amazonaws.com/accounts/1/products/imported/Star-Wars-Ships-t-shirt-Star-Wars-500x500.jpg" alt="Star Wars" width="25%" id="p2">
      <img src="https://honeysanime.com/wp-content/uploads/2016/06/Harry-Potter-movie-Wallpaper-500x500.jpg" alt="HarryPotter" width="25%" id="p3">
      <img src="https://media.aintitcool.com/media/uploads/2019/prometheus/el-camino-poster.jpg" alt="EI Camino" width="25%" id="p4">
    </div>
    </div>
</template>

<style scoped>
#background {
  width: 100%;
  height: auto;
}

.background {
  height: 100%;
}

#cover {
  display: flex;
  justify-content: center;
  align-items: center;
}

#p1 {
  width: 25%;
  height: 40%;
  position: absolute;
  bottom: 25%;
  left: 0%;
}

#p2 {
  width: 25%;
  height: 40%;
  position: absolute;
  bottom: 25%;
  left: 25%;
}

#p3 {
  width: 25%;
  height: 40%;
  position: absolute;
  bottom: 25%;
  left: 50%;
}

#p4 {
  width: 25%;
  height: 40%;
  position: absolute;
  bottom: 25%;
  left: 75%;
}
</style>