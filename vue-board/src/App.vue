<script>
import NavBar from "@/components/comm/NavBar.vue";

export default {
  name: 'App',
  components: {NavBar},
  data() {
    return {
      drawer: false,
      title: '개발자들을 위한 커뮤니티 플렛폼',
      footImg: require(`@/assets/images/tan.png`),
      author: '',
    }
  },
  // created() {
  //   const user = JSON.parse(this.$store.getters['userStore/getUserInfo'])
  //   this.author = user.author
  // },
  methods: {
    close() {
      this.drawer = false;
    }
  }
}
</script>

<template>
  <v-app>
    <v-app-bar elevation="3">
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
      <v-toolbar-title @click="this.$router.push('/')">{{title}}</v-toolbar-title>
      <template v-slot:append>
        {{author}}
      </template>
    </v-app-bar>

    <NavBar v-model="drawer" :user="drawer" @close="close"/>

    <v-main class="bg-grey-darken-3">
      <v-container style="width: 70%">
       <router-view />
      </v-container>
    </v-main>

     <v-card
          tile
          width="100%"
          height="90px"
          class="d-flex align-center justify-center"
      >
        <v-img
            class="mx-auto"
            height="80"
            max-width="100"
            :src="footImg"
        />
      </v-card>
  </v-app>
</template>