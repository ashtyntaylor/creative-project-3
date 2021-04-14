<template>
<div class="library">
  <h1>Manage My Library</h1>
    <div class="heading">
      <h1>-Add Movie-</h1>
    </div>
    <div class="add">
      <div class="form">
        <input v-model="title" placeholder="Title">
        <br />
        <input v-model="genre" placeholder="Genre">
        <br />
        <input v-model="duration" placeholder="Duration (minutes)">
        <br />
        <input v-model="starring" placeholder="Actor Name">
        <br />
        <textarea v-model="description" placeholder="Description" />
        <br />
        <input v-model="path" placeholder="Full HTTP file path"/>
        <button @click="upload">Upload</button>
      </div>
      <div class="upload" v-if="addMovie">
        <h2>{{addMovie.title}}</h2>
        <h3>{{addMovie.genre}}</h3>
        <h3>{{addMovie.duration}}</h3>
        <h3>{{addMovie.starring}}</h3>
        <h3>{{addMovie.description}}</h3>
        <img :src="addMovie.path"/>
      </div>
    </div>
    <div class="heading">
      <h1>-Edit/Delete Movie-</h1>
    </div>
    <div class="edit">
      <div class="form">
        <div class="suggestions" v-if="suggestions.length > 0">
          <div class="suggestion" v-for="s in suggestions" :key="s.id" @click="selectMovie(s)">{{s.title}}
          </div>
        </div>
      </div>
      <div class="upload" v-if="findMovie">
        <input v-model="findMovie.title" placeholder="Title">
        <br />
        <input v-model="findMovie.genre" placeholder="Genre">
        <br />
        <input v-model="findMovie.duration" placeholder="Duration (minutes)">
        <br />
        <input v-model="findMovie.starring" placeholder="Actor name">
        <br />
        <textarea v-model="findMovie.description" placeholder="Enter a description"/>
        <p></p>
        <img :src="findMovie.path"/>
      </div>
      <div class="actions" v-if="findMovie">
        <button @click="deleteMovie(findMovie)">Delete</button>
        <br />
        <br />
        <button @click="editMovie(findMovie)">Edit</button>
      </div>
    </div>
</div>
</template>

<style scoped>
h1 {
  text-align: center;
}
/* Suggestions */
.suggestions {
  width: 200px;
  border: 1px solid #ccc;
}

.suggestion {
  min-height: 20px;
}

.suggestion:hover {
  background-color: #cce6ff;
}
.image h2 {
  font-style: italic;
  font-size: 1em;
}

.heading {
  display: flex;
  margin-top: 20px;
}

.heading h2 {
  margin-top: 8px;
}

.add,
.edit {
  display: flex;
}

/* Form */
input,
textarea,
select,
button {
  font-family: 'Montserrat', sans-serif;
  font-size: 1em;
}

.form {
  margin-right: 50px;
}

input {
  margin-bottom: 20px;
}


/* Uploaded images */
.upload h2 {
  margin: 0px;
}

.upload img {
  max-width: 300px;
}
</style>

<script>
export default {
  name: 'Library',
  data() {
    return {
      title: "",
      description: "",
      genre: "",
      duration: null,
      starring: "",
      path: "",
      addMovie: null,
      movies: this.$root.$data.movies,
      findTitle: "",
      findMovie: null,
    }
  },
  created() {
    //this.getMovies();
  },
  computed: {
    suggestions() {
      let movies = this.movies.filter(movie => movie.title.toLowerCase().startsWith(this.findTitle.toLowerCase()));
      return movies.sort((a, b) => a.title > b.title);
    }
  },
  methods: {
    editMovie(movie) {

      for(var i=0; i < this.movies.length; i++){
        if(this.movies[i].id == movie.id){
          this.movies[i] = movie;
        }
      }

      return true;
    },
    selectMovie(movie) {
      this.findTitle = "";
      this.findMovie = movie;
    },
    deleteMovie(movie) {

      for(var i=0; i < this.movies.length; i++){
        if(this.movies[i].id == movie.id){
          this.movies.splice(i, 1);
          return;
        }
      }
      this.findMovie = null;
      return true;
    },
    upload() {

        this.movies.push({
          title: this.title,
          genre: this.genre,
          duration: this.duration,
          starring: this.starring,
          description: this.description,
          path: this.path,
        });
        this.addMovie = this.movies[this.movies.length];
    },
  }
}
</script>
