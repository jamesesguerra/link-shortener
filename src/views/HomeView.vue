<template>

  <main class="py-16">

    <v-container class="fluid container text-center">
      <div class="landing">
         <h1 class="white--text">Create <span class="accentt">links</span> that fit right in your <span class="accentt">pocket</span></h1>
      <p class="white--text">These links are created by the most widely trusted link management platform in the world.</p>
      </div>
    </v-container>

    <v-container class="fluid container text-center">
      <div class="form">
        <v-text-field
            v-model="url"
            solo
            label="Enter your URL"
            clearable
            class="mr-3"
          ></v-text-field>
          <v-btn 
            x-large 
            depressed
            @click="shorten"
          >shorten</v-btn>
      </div>
    </v-container>

    <v-container v-if="loading" class="fluid container text-center">
      <v-progress-circular
      :size="50"
      color="red accent-1"
      indeterminate
      ></v-progress-circular>
    </v-container>

    <v-container v-if="returned" class="fluid container text-center white--text">
      <h2>Your shortened URL:</h2>
      <p class="shortened">{{ shortenedUrl }}</p>
    </v-container>

  </main>


  


  
</template>

<script>

  export default {
    name: 'Home',

    data() {
      return {
        returned: false,
        loading: false,
        url: '',
        shortenedUrl: '',
      }
    },
    methods: {
      async shorten() {
        this.returned = false;
        this.loading = true;
        const urlData = {
          domain: "bit.ly",
          long_url: this.url,
        }

        const response = await fetch('https://api-ssl.bitly.com/v4/shorten', {
          method: 'POST',
          headers: {
            'Content-Type': 'application/json',
            'Authorization': 'Bearer 38b5e21a99a8ad19b58ae0d0e8c9fd27c17de15c'
          },
          body: JSON.stringify(urlData)
        })

        const data = await response.json();
        this.loading = false;
        this.returned = true;
        this.shortenedUrl = data.link;
        this.url = ''
      }
    }
  }
</script>

<style scoped>
.v-btn {
  height: 100%;
}

main {
  background-color: #011747;
}
</style>
