<template>
  <div class="card">
    <div class="card-header">
      <strong>{{ profile.profile.Comments.length }}</strong> 已評論餐廳
    </div>
    <div class="card-body">
      <router-link
        v-for="Comment in profile.profile.Comments"
        v-bind:key="Comment.id"
        v-bind:to="{ name: 'restaurant', params: { id: Comment.RestaurantId } }"
      >
        <img
          v-bind:src="Comment.Restaurant.image"
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
  name: "UserCommentsCard",
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