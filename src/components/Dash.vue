<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="12" sm="6" lg="3" v-for="n in cardData" :key="n.icon">
        <ccard :cardData="n"></ccard>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="12" md="7">
        <MyChart :data="chartData[0]"></MyChart>
      </v-col>
      <v-col cols="12" md="5"> <MyChart :data="chartData[2]"></MyChart> </v-col>
      <v-col>
        <MyChart :data="chartData[1]"></MyChart>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import MyChart from "./chart";
import ccard from "./ccard.vue";
import { mapState } from "vuex";
export default {
  components: { ccard, MyChart },
  name: "Dash",
  data() {
    return {};
  },

  computed: {
    ...mapState(["cardData", "chartData"]),
  },
};
</script>
