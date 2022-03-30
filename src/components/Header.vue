<template>    
    <nav>
        <v-app-bar flat class="container fluid">
            <v-app-bar-title class="white--text">
                PocketURL
            </v-app-bar-title>
            <v-spacer></v-spacer>
            <a href="https://dev.bitly.com/" target="_blank">
                <v-btn depressed>Bitly API</v-btn>
            </a>
        </v-app-bar>
    </nav>
</template>

<script>
export default {

}
</script>

<style scoped>
nav, .v-app-bar {
    background-color: #011747 !important;
    font-family: 'Montserrat';
}


</style>