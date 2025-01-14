<template>
  <div class="event" :class="{ show: isOpen }">
    <p>{{ text }}</p>
    <button @click="isOpen = false">X</button>
  </div>
</template>
<script>
export default {
  name: "EventComponent",
  props: {
    text: String,
    isEventOpen: Boolean,
  },
  data() {
    return {
      isOpen: true,
    };
  },
};
</script>
<style>
.event {
  display: none;
  background-color: #444;
  color: #fff;
  padding: 10px 20px;
  text-align: center;
  font-size: 1.2rem;
  justify-content: space-between;
  align-items: center;
}
.show {
  display: flex;
}
.event button {
  margin: 0;
  background-color: transparent;
  border: none;
  color: #fff;
  font-size: 1.2rem;
  cursor: pointer;
}
.event p {
  margin: 0;
}
</style>
