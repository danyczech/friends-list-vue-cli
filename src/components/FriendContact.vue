<template>
  <li>
    <h2>{{ name }} {{ isFavorite ? " (Favorite)" : "" }}</h2>
    <button @click="toggleDetails">
      {{ detailsVisible ? "Hide" : "Show" }} Details
    </button>
    <button @click="toggleFavorite">
      {{ isFavorite ? "Not" : "Is" }} Favorite
    </button>
    <ul v-if="detailsVisible">
      <li><strong>Phone:</strong>{{ phoneNumber }}</li>
      <li><strong>E-mail:</strong>{{ emailAddress }}</li>
    </ul>
    <button @click="$emit('delete-contact', id)">Delete</button>
  </li>
</template>

<script>
export default {
  props: ["id", "name", "phoneNumber", "emailAddress", "isFavorite"],
  emits: ["toggle-favorite", "delete-contact"],
  data() {
    return {
      detailsVisible: false,
    }
  },
  methods: {
    toggleDetails() {
      this.detailsVisible = !this.detailsVisible
    },
    toggleFavorite() {
      this.$emit("toggle-favorite", this.id)
    },
  },
}
</script>
