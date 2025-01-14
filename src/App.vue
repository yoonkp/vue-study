<template>
  <Event :text="text" />
  <Navbar />
  <Movies
    :data="data"
    @openModal="
      isModal = true;
      selectedMovie = $event;
    "
    @addLike="addLike($event)"
  />
  <!--
    Movies 컴포넌트를 불러올 때, props로 data를 전달합니다.
    이벤트를 받아서 isModal을 true로 변경하고, selectedMovie에 $event를 할당합니다.
  -->
  <Modal :data="data" :isModal="isModal" :selectedMovie="selectedMovie" @closeModal="isModal = false" />
  <!--
    Modal 컴포넌트를 불러올 때, props로 data, isModal, selectedMovie을 전달합니다.
    이벤트를 받아서 isModal을 false로 변경합니다.
  -->
</template>

<script>
import data from "./assets/movies";
import Movies from "./components/Movies.vue";
import Navbar from "./components/Navbar.vue";
import Modal from "./components/Modal.vue";
import Event from "./components/Event.vue";
console.log(data);
export default {
  name: "App",
  data() {
    return {
      isModal: false,
      data: data,
      selectedMovie: 0,
      text: "이벤트입니다.",
    };
  },
  methods: {
    addLike(i) {
      this.data[i].like++;
    },
  },
  components: {
    Navbar: Navbar,
    Modal: Modal,
    Movies: Movies,
    Event: Event,
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
}

body {
  max-width: 768px;
  margin: 0 auto;
  padding: 20px;
}

h1,
h2,
h3 {
  margin-bottom: 1rem;
}

p {
  margin-bottom: 0.5rem;
}

button {
  margin-right: 10px;
  margin-top: 1rem;
}

.movie {
  width: 100%;
  border: 1px solid #ccc;
  display: flex;
  margin-bottom: 20px;
  padding: 1rem;
}

.movie figure {
  width: 30%;
  margin-right: 1rem;
}

.movie img {
  width: 100%;
}

.movie .info {
  width: 100%;
}

.modal {
  background: rgba(0, 0, 0, 0.7);
  position: fixed;
  left: 0;
  top: 0;
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal .inner {
  background: #fff;
  width: 80%;
  padding: 20px;
  border-radius: 10px;
}
</style>
