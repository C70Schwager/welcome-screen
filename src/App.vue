<script>
import Card from './Card.vue';
import Footer from './Footer.vue';

export default {
  name: "App",
  components:{
    Card,
    Footer 
  },

   data() {
    return {
      title: "Welcome to Opportunity",
      date: new Date().toDateString(),
      sheet_id: import.meta.env.VITE_GOOGLE_SHEET_ID,
      api_token: import.meta.env.VITE_GOOGLE_API_KEY,
      entries: []
    };
  },

  computed: {
    gsheet_url() {
      return `https://sheets.googleapis.com/v4/spreadsheets/${this.sheet_id}/values:batchGet?ranges=A2%3AE100&valueRenderOption=FORMATTED_VALUE&key=${this.api_token}`;
}
},

  methods: {
    async getData() {
      const response = await fetch(this.gsheet_url);
      const data = await response.json();
      this.entries = data.valueRanges[0].values;
      console.log(this.entries)
    }
},

mounted() {
    this.getData(); // get first initial data and then wait for the next update
  },
};

</script>


<template>

  <div>

      <div id="application">

        <h1 class="site-title">{{ title }}</h1>
        <h2 class="site-title">{{ date }}</h2>
      </div>

      <ul>
        <Card v-for="entry in entries">
          <template #time>{{ entry[0] }}</template>
          <template #date>{{ entry[1] }}</template>
          <template #title>{{ entry[2] }}</template>
          <template #desciption>{{ entry[3] }}</template>
        </Card>
      </ul>

      <footer>
        <img src="src/assets/STZH_SEB_Logo.png" alt="STZH Logo">
        <img src="src/assets/Opportunity.png" alt="Opportunity Logo">
        <img src="src/assets/SAG_Logo_De.png" alt="SAG Logo">
      </footer>

    </div>

</template>

<style>
#application {
  font-family: "Inter", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #323d4a;
  margin: 60px;
}
body {
  width: 1080px;
  height: 1920px;
  background-color: rgba(232, 239, 244, 1);
  ;
}
.site-title {
  color: rgba(0, 0, 0, 0.7);
  margin-left: 60px;
}
h1 .site-title{
  color: rgba(50, 61, 74, 1);
  font-family: Inter;
  font-size: 62px;
  font-weight: 900;
  line-height: 75px;
  letter-spacing: 0em;
  text-align: left;  
}

h2 .site-title{
  color: rgba(154, 167, 177, 1);
  font-family: Inter;
  font-size: 62px;
  font-weight: 500;
  line-height: 75px;
  letter-spacing: 0em;
  text-align: left;
}

</style>
