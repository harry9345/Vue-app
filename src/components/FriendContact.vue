<template>
  <li>
    <h2>{{ name }} {{ isFavorit ? '(Favorit)': ''}}</h2>
    <button @click="toggleFavorit">toglle</button>
    <button @click="toggleDetails">{{ visibility? "Hide":"Show"}} Details</button>
    <ul v-if="detailsAreVisible">
      <li>
        <strong>Phone:</strong>
        {{phoneNumber }}
      </li>
      <li>
        <strong>Email:</strong>
        {{ emailAddress }}
      </li>
    </ul>
    <button @click="$emit('delete',id)">Delete</button>
  </li>
</template>
<script>
export default {
  // props: ["name", "phoneNumber", "emailAddress"],
  props: {
    id: {
      type: String
    },
    name: {
      type: String,
      required: true
    },
    phoneNumber: {
      type: String,
      required: true
    },
    emailAddress: {
      type: String,
      required: true
    },
    isFavorit: {
      type: Boolean,
      required: false,
      default: false
    }
  },
  emits: ["toggleFavorit", "delete"],
  // emits: {
  //   toggleFavorit: function(id) {
  //     if (id) {
  //       return true;
  //     } else {
  //       console.warn("missing");
  //       return false;
  //     }
  //   }
  // },
  data() {
    return {
      detailsAreVisible: false
    };
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    toggleFavorit() {
      this.$emit("toggle-favorit", this.id);
    }
  }
};
</script>