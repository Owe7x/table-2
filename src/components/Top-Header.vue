<template>
  <div>
    <div class="top-header">LOGGED IN</div>
    <div v-if="loggedIn" class="top-header">YES</div>
    <div v-else class="top-header">NO</div>
    <button class="but" @click="signOut">Sign out</button>
  </div>
</template>

<script>
import * as firebase from "firebase/app";
import "firebase/auth";
export default {
  name: "top-header",
  mounted() {
    this.setupFirebase();
  },
  methods: {
    setupFirebase() {
      firebase.auth().onAuthStateChanged(user => {
        if (user) {
          // User is signed in.
          console.log("signed in");
          this.loggedIn = true;
        } else {
          // No user is signed in.
          this.loggedIn = false;
          console.log("signed out", this.loggedIn);
        }
      });
    },
    signOut() {
      firebase
        .auth()
        .signOut()
        .then(() => {
          this.$router.replace({ name: "login" });
        });
    }
  },
  data() {
    return {
      loggedIn: false
    };
  }
};
</script>

<style lang="scss" scoped>
div {
  color: inherit;
}
.top-header {
  font-weight: bold;
  margin-bottom: 5px;
}
.but {
  padding: 5px 15px;
  background-color: transparent;
  text-transform: uppercase;
}
</style>