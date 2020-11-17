<template>
  <v-app>
    <v-main>
      <router-view />
    </v-main>
    <BottomNavigation />
  </v-app>
</template>

<script>
import HelloWorld from "./components/HelloWorld";
import BottomNavigation from "@/components/BottomNavigation";

export default {
  name: "App",

  components: {
    // eslint-disable-next-line vue/no-unused-components
    HelloWorld,
    BottomNavigation
  },

  
};
</script>
<style>

</style>
