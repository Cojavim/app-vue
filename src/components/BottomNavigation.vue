<template>
    <v-bottom-navigation v-model="value">
        <router-link :to="{ name: 'Chart' }">
            <v-btn value="recent">
                <span>Chart</span>
                <v-icon>mdi-chart-areaspline-variant</v-icon>
            </v-btn>
        </router-link>

        <router-link :to="{ name: 'Home' }">
            <v-btn value="favorites">
                <span>Home</span>
                <v-icon>mdi-home</v-icon>
            </v-btn>
        </router-link>
        <router-link :to="{ name: 'Table' }">
            <v-btn value="nearby">
                <span>Table</span>
                <v-icon>mdi-table</v-icon>
            </v-btn>
        </router-link>
    </v-bottom-navigation>
</template>

<script>
export default {
    name: "BottomNavigation",
    components: {
    },
    data: () => ({ value: 'recent' }),
}
</script>

<style>
    a {
    text-decoration: none;
    color: inherit;
    }
</style>