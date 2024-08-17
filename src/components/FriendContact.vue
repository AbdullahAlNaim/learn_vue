<template>
  <li>
    <h2>{{ name }} {{ isFav ? '(Favorite)' : '' }}</h2>
    <button @click="toggleFav">Toggle Favorites</button>
    <button @click="toggleDetails">{{ detailShow ? 'Hide' : 'Show' }} Details</button>
    <ul v-if="detailShow">
      <li>Phone: {{ phoneNumber }}</li>
      <li>Email: {{ emailAddress }}</li>
    </ul>
  </li>
</template>

<script>
export default {
  // props: [
  //   'name',
  //   'phoneNumber',
  //   'emailAddress',
  //   'isFav',
  // ],
  props: {
    id: {
      type: String,
      required: true,
    },
    name: {
      type: String,
      required: true,
    },
    phoneNumber: {
      type: String,
      required: true,
    },
    emailAddress: {
      type: String,
      required: true,
    },
    isFav: {
      type: Boolean,
      required: false,
      default: false,
      // validator: function(value) {
      //   return value === '1' || value === '0';
      // }
    },
  },
  emits: [
    'toggle-fav'
  ],
  // emits: {
  //   'toggle-fav': function(id) {
  //     if (id) {
  //       return true;
  //     } else {
  //       console.warn("Id is missing")
  //       return false;
  //     }
  //   },
  // },
  data() {
    return {
      detailShow: false,
    }
  },
  methods: {
    toggleDetails() {
      this.detailShow = !this.detailShow
      this.phoneNumber
    },
    toggleFav() {
      this.$emit('toggle-fav', this.id);
    }
  }
};
</script>