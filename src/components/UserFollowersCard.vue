<template>
  <div class="card">
    <div class="card-header">
      <strong>{{ profile.profile.Followers.length }}</strong> followers (追隨者)
    </div>
    <div class="card-body">
      <router-link
        v-for="Followers in profile.profile.Followers"
        v-bind:key="Followers.id"
        v-bind:to="{ name: 'user', params: { id: Followers.id } }"
      >
        <img
          v-bind:src="Followers.image"
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
  name: "UserFollowersCard",
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

