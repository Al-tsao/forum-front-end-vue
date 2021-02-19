<template>
  <div class="row no-gutters">
    <div class="col-md-4">
      <img v-bind:src="profile.profile.image" width="300px" height="300px" />
    </div>
    <div class="col-md-8">
      <div class="card-body">
        <h5 class="card-title">{{ profile.profile.name }}</h5>
        <p class="card-text">{{ profile.profile.email }}</p>
        <ul class="list-unstyled list-inline">
          <li>
            <strong>{{ profile.profile.Comments.length }}</strong> 已評論餐廳
          </li>
          <li>
            <strong>{{ profile.profile.FavoritedRestaurants.length }}</strong>
            收藏的餐廳
          </li>
          <li>
            <strong>{{ profile.profile.Followings.length }}</strong>
            followings (追蹤者)
          </li>
          <li>
            <strong>{{ profile.profile.Followers.length }}</strong> followers
            (追隨者)
          </li>
        </ul>
        <p></p>
        <form
          action="/following/2?_method=DELETE"
          method="POST"
          style="display: contents"
        >
          <template v-if="profile.profile.id === user.currentUser.id">
            <button type="submit" class="btn btn-primary">Edit</button>
          </template>
          <template v-else>
            <button
              v-if="profile.isFollowed"
              type="submit"
              class="btn btn-danger"
              v-on:click.stop.prevent="deleteFollow(profile)"
            >
              取消追蹤
            </button>
            <button
              v-else
              type="submit"
              class="btn btn-primary"
              v-on:click.stop.prevent="addFollow(profile)"
            >
              新增追蹤
            </button>
          </template>
        </form>
        <p></p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "UserProfileCard",
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
    addFollow(profile) {
      profile.isFollowed = true;
    },
    deleteFollow(profile) {
      profile.isFollowed = false;
    },
  },
  created() {
    this.fetchUserProfileCard();
  },
};
</script>