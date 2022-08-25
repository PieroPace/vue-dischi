<template>
  <main class="container pb-4">
    <div class="container" v-if="albums">
      <div class="row">
        <Select
          :type="'Genere'"
          :array="genres"
          @changeValue="changeGenre($event)"
        />
        <Select
          :type="'Artista'"
          :array="artists"
          @changeValue="changeArtist($event)"
        />
      </div>
      <div class="row row-cols-6 gap-3">
        <Album
          v-for="(album, index) in filteredAlbums"
          :key="index"
          :album="album"
        />
      </div>
    </div>
    <div class="row text-center text-white" v-else>
      <div class="col-12">
        <h1>Loading...</h1>
      </div>
    </div>
  </main>
</template>

<script>
import axios from "axios";
import Album from "./Album.vue";
import Select from "./Select.vue";

export default {
  name: "Main",
  components: {
    Album,
    Select,
  },
  data() {
    return {
      albums: null,
      filteredAlbums: null,
      genres: null,
      artists: null,
      selected: "All",
      queryApi: "https://flynn.boolean.careers/exercises/api/array/music",
    };
  },
  mounted() {
    this.getAlbums();
  },
  methods: {
    getAlbums() {
      setTimeout(() => {
        axios
          .get(this.queryApi)
          .then((result) => {
            this.albums = result.data.response;
            this.getGenre();
            this.getArtists();
            this.filteredAlbums = this.albums;
          })
          .catch((error) => {
            console.log(error);
          });
      }, 1000);
    },
    getGenre() {
      const genresArray = [];
      for (let i = 0; i < this.albums.length; i++) {
        const element = this.albums[i];
        while (!genresArray.includes(element.genre)) {
          genresArray.push(element.genre);
        }
      }
      this.genres = genresArray;
    },
    getArtists() {
      const artistsArray = [];
      for (let i = 0; i < this.albums.length; i++) {
        const element = this.albums[i];
        while (!artistsArray.includes(element.author)) {
          artistsArray.push(element.author);
        }
      }
      this.artists = artistsArray;
    },
    changeGenre(selected) {
      this.selected = selected;
      if (this.selected == "" || this.selected == "All") {
        this.filteredAlbums = this.albums;
      } else {
        this.filteredAlbums = this.albums.filter((album) => {
          return album.genre == this.selected;
        });
      }
    },
    changeArtist(selected) {
      this.selected = selected;
      if (this.selected == "" || this.selected == "All") {
        this.filteredAlbums = this.albums;
      } else {
        this.filteredAlbums = this.albums.filter((album) => {
          return album.author == this.selected;
        });
      }
    },
  },
};
</script>

<style scoped lang="scss"></style>
