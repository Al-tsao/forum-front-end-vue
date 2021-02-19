<template>
  <div class="card">
    <div class="card-header">
      <strong>{{ profile.profile.FavoritedRestaurants.length }}</strong>
      收藏的餐廳
    </div>
    <div class="card-body">
      <router-link
        v-for="FavoritedRestaurant in profile.profile.FavoritedRestaurants"
        v-bind:key="FavoritedRestaurant.id"
        v-bind:to="{
          name: 'restaurant',
          params: { id: FavoritedRestaurant.id },
        }"
      >
        <img
          v-bind:src="FavoritedRestaurant.image"
          width="60"
          height="60"
          class="avatar"
        />
      </router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: "UserFavoritedRestaurantsCard",
  props: {
    initialProfile: {
      type: Object,
      required: true,
    },
    initialUser: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      profile: {},
      user: {},
    };
  },
  methods: {
    fetchUserProfileCard() {
      this.profile = { ...this.initialProfile };
      this.user = { ...this.initialUser };
      console.log("test", this.initialUser);
    },
  },
  created() {
    this.fetchUserProfileCard();
  },
};
</script>