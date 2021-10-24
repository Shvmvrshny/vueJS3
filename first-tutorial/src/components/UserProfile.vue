<template>
  <div class="user_prof_top">
    <div class="user_prof__name">@{{ user.username }}</div>

    <!-- <div> - {{ fullName }}</div> -->
    <span class="user_prof__followers">Followers : {{ followers }}</span>
    <div v-if="user.isAdmin" class="admin__badge">Admin</div>
    <div>
      <button v-on:click="followUser">Follow</button>
    </div>
    <div class="user_prof__twoots" v-for="twoot in user.twoots" :key="twoot.id">
      {{ twoot.content }}
    </div>
  </div>
</template>

<script>
export default {
  name: "UserProfile",
  data() {
    return {
      followers: 444,
      user: {
        id: 1,
        username: "shvmvrshny",
        firstname: "Shivam",
        lastname: "Varshney",
        email: "shvmvrshny@gmailÎ.com",
        isAdmin: true,
        twoots: [
          { id: 1, content: "Hello world" },
          { id: 2, content: "Hello world again!" },
        ],
      },
    };
  },
  watch: {
    followers(newFollowerCount, oldFollowerCount) {
      if (oldFollowerCount < newFollowerCount) {
        console.log(`${this.user.username} one new follower detected!`);
      }
    },
  },
  computed: {
    fullName() {
      return `${this.user.firstname} ${this.user.lastname}`;
    },
  },
  methods: {
    followUser() {
      this.followers++;
    },
  },
  mounted() {
    this.followUser();
  },
};
</script>

<style scoped>
.user_prof_top {
  padding: 10px;
  border: 0.5px solid rgba(0, 0, 0, 0.233);
  width: fit-content;
  border-radius: 4px;
  background-color: white;
  margin: 20px;
}
.user_prof__name {
  font-size: 2vh;
  font-weight: 600;
}

.user_prof__followers {
  font-size: 14px;
  font-weight: 500;
}
.admin__badge {
  font-size: 11px;
  color: white;
  background-color: rebeccapurple;
  padding: 2px 8px;
  width: fit-content;
  border-radius: 5px;
  margin-top: 5px;
  font-weight: 600;
}
</style>