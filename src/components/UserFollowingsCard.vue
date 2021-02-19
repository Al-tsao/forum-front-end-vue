<template>
  <div class="card">
    <div class="card-header">
      <strong>{{ profile.profile.Followings.length }}</strong> followings
      (追蹤者)
    </div>
    <div class="card-body">
      <router-link
        v-for="Following in profile.profile.Followings"
        v-bind:key="Following.id"
        v-bind:to="{ name: 'user', params: { id: Following.id } }"
      >
        <img
          v-bind:src="Following.image"
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
  name: "UserFollowingsCard",
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