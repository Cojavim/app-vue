<template>
    <div>
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
            <v-btn @click="sheet = !sheet">
                <span>Bug Report</span>
                <v-icon>mdi-bug</v-icon>
            </v-btn>
        </v-bottom-navigation>
        <v-bottom-sheet v-model="sheet">
            <v-sheet
                class="text-center"
                height="200px"
            >
                <v-btn
                class="mt-6"
                text
                color="red"
                @click="sheet = !sheet"
                >
                close
                </v-btn>
                <div class="py-3">
                Just tell me.
                </div>
            </v-sheet>
        </v-bottom-sheet>
    </div>
</template>

<script>
export default {
    name: "BottomNavigation",
    components: {
    },
    data: () => ({ 
        value: 'recent',
        sheet: false, 
    }),
}
</script>

<style>
    a {
    text-decoration: none;
    color: inherit;
    }
</style>