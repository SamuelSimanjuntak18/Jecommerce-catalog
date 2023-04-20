<template>
  <div class="container">
    <h1 style="color:white;">One step closer To Your Favorite Movies </h1> <br>
    <div class="row">
      <div
        v-for="(show, index) in shows"
        :key="index"
        class="col-sm mb-3"
        style="padding-top: 10px; padding-bottom: 10px;"
      >
        <div class="card" style="width: 25rem; border: 1px solid gray; box-shadow: 2px 2px 4px gray;">
          <img
            v-if="show.image"
            :src="show.image.medium"
            class="card-img-top image-clickable"
           :alt="`Poster for ${show.name}`"
            style="max-width: 100%; height: auto; object-fit: cover;"
          />
          <div class="card-body"> 
            <h5 class="card-title">{{ show.name }}</h5>
            <button class="btn btn-primary" @click="showDetails(show)">
              <a :href="show.url" target="_blank" class="btn btn-primary" style="text-decoration: none;">Baca Selengkapnya</a>
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<style>
body {
  background-color:black;
}
.image-clickable {
  cursor: pointer;
  transition: transform 0.2s;
}

.image-clickable:hover {
  transform: scale(1.1);
}
</style>
<script>
export default {
  data() {
    return {
      shows: [],
    };
  },
  mounted() {
    fetch("http://api.tvmaze.com/search/shows?q=girls")
      .then((response) => response.json())
      .then((data) => {
        this.shows = data.map((result) => ({
          ...result.show,
          url: result.show.officialSite || result.show.url,
        }));
      });
  },
  methods: {
    showDetails(show) {
      console.log(show);
    },
  },
};

</script>











