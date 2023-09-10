<script>
export default {
  name: "App",
  data() {
    return {
      title: "Welcome to Opportunity",
      sheet_id: import.meta.env.VITE_GOOGLE_SHEET_ID,
      api_token: import.meta.env.VITE_GOOGLE_API_KEY,
      entries: []
    };
  },
  computed: {
	gsheet_url() {
return `https://sheets.googleapis.com/v4/spreadsheets/${this.sheet_id}/values:batchGet?ranges=A1%3AE100&valueRenderOption=FORMATTED_VALUE&key=${this.api_token}`;
}
},
  methods: {
      async getData() {
        const response = await fetch(this.gsheet_url);
        const data = await response.json();
        this.entries = data.valueRanges[0].values;
      }
  },
  mounted() {
    this.getData(); // get first initial data and then wait for the next update
  },
};
</script>
<template>
  <div id="app">
    <h1 class="site-title">{{ title }}</h1>
    <h2>00.00.0000</h2>

        <!-- Das Rechteck -->
    <div class="container">
      <!-- Uhrzeit (rot) -->
      <div class="time">
        <h3>Uhrzeit: 15:30 Uhr</h3>
      </div>
      <!-- Beschreibung (orange) -->
      <div class="description">
        <h4>Beschreibung des Anlasses!</h4>
      </div>
      <!-- Text (orange) -->
      <div class="text">
        <p>Die zweite Klasse kommt auf Besuch!</p>
      </div>
    </div>

    <br>

            <!-- Das Rechteck -->
            <div class="container">
              <!-- Uhrzeit (rot) -->
              <div class="time">
                <h3>Uhrzeit: 15:30 Uhr</h3>
              </div>
              <!-- Beschreibung (orange) -->
              <div class="description">
                <h4>Beschreibung des Anlasses!</h4>
              </div>
              <!-- Text (orange) -->
              <div class="text">
                <p>Die zweite Klasse kommt auf Besuch!</p>
              </div>
            </div>

            <br>

                    <!-- Das Rechteck -->
    <div class="container">
      <!-- Uhrzeit (rot) -->
      <div class="time">
        <h3>Uhrzeit: 15:30 Uhr</h3>
      </div>
      <!-- Beschreibung (orange) -->
      <div class="description">
        <h4>Beschreibung des Anlasses!</h4>
      </div>
      <!-- Text (orange) -->
      <div class="text">
        <p>Die zweite Klasse kommt auf Besuch!</p>
      </div>
    </div>


    <footer>

    </footer>

  </div>

 
</template>



<style>
#app {
  font-family: "Inter", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #323d4a;
  margin: 60px;
  background-color: rgba(232, 239, 244, 1)}

.site-title {
  width: 764px;
  height: 75px;
  top: 69px;
  left: 60px;

  font-size: 62px;
  font-weight: 900;
  line-height: 75px;
  letter-spacing: 0em;
  text-align: left;
}

h2 {
  width: 335px;
  height: 75px;
  top: 165px;
  left: 60px;

  font-size: 62px;
  font-weight: 500;
  line-height: 75px;
  letter-spacing: 0em;
  text-align: left;
  color: rgba(154, 167, 177, 1);
}

footer {
  width: 1080px;
  height: 130px;
  top: 1790px;
}

  /* Stil für das Rechteck */
  .container {
    width: 729px;
    height: 182px;
    background-color: rgba(15, 5, 160, 1);
  }

  /* Stil für das Datum/Uhrzeit (rot) */
  .time h3 {
    color: #EB5E00;
    font: bold;
    margin: 0;
  }

  /* Stil für die Beschreibung (orange) */
  .description h4 {
    color: #FFBFAB;
    font: bold;
    margin: 0;
  }

  /* Stil für den Text (orange) */
  .text p {
    color: #FFBFAB;
    margin: 0;
  }
</style>
