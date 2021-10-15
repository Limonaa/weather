<template>
  <v-app>
    <v-row>
    <v-col>
   <div 
   class="locate-container"
   >
   <v-text-field
   elevation="4"
   id="locate-input"
    label="LOCATE"
    outlined
    shaped
    >
    </v-text-field>
   </div>
    </v-col>
    <v-col>
   <div>
    <v-btn
    id="btn"
    @click="start"
    elevation="2"
    icon
    x-large
    >
    </v-btn>
   </div>
    </v-col>
    </v-row>
   <div
   class="weather-con"
    >
    <v-card
    width="100%"
    height="400"
    outlined
    elevation="4"
    >
    <v-card-title
    id="title"
    class="justify-center"
    color="white"
    >
    {{locate}}
    </v-card-title>
    <v-card-subtitle
    id="subtitle"
    class="date"
    color="white"
    >
    {{today}}
    </v-card-subtitle>
    <h1>9*</h1>
    </v-card>
   </div>
  </v-app>
</template>

<script>

export default {
  name: 'App',

  data() {
    return {
      months: ['January', 'February', 'March', 'April', 'May', 'June',
      'July', 'August', 'September', 'October', 'November', 'December'],
      locate: ' ',
      today: '',
    }
  },
  methods: {
    start() {
      let city = document.getElementById('locate-input').value;
      this.locate = city;
      var date = new Date();
      let day = date.getDate();
      let month = this.months[date.getMonth()];
      let year = date.getFullYear();
      this.today = `${day}  ${month}  ${year}`;
    }
  }
};
</script>
<style scoped>
.locate-container {
  width: 70%;
  height: 5%;
  margin: auto;
  margin-left: 61%;
  margin-top: 17rem;

}
.date {
  text-align: center;
}
#title {
  margin-top: 0.8rem;
  margin-bottom: 0.3rem;
  font-weight: bold;
  font-size: 2em;
}
#subtitle {
  font-size: 1em;
}
.temp-box {
  background-color: #7c7c7c98;
}
h1 {
  text-align: center;
  font-size: 8em;
  font-family: 'Roboto', sans-serif;
}
.weather-con {
  width: 40%;
  height: 60%;
  margin: auto;
}
#btn {
  margin-top: 41%;
  margin-left: 31%;
  margin-bottom: 0;
}
</style>