<template>
  <v-container>
    <v-row>
      <v-col class="text-center">
        <p>Send a WhatsApp direct without adding to your contact list</p>
      </v-col>
    </v-row>
    <v-row justify="center">
      <v-col cols="10" md="6">
        <v-text-field
          solo-inverted
          v-model="phone"
          type="number"
          label="Phone Number"
          counter="14"
          :rules="[
            (v) => !!v || 'Phone number is required',
            (v) => !!v && v.length < 8 && 'Phone number is short',
          ]"
          required
        ></v-text-field>
      </v-col>
      <v-col cols="10" class="text-center"
        ><v-btn @click="routeToWhatsApp" color="#1DBEA5" class="white--text"
          >Message now !
        </v-btn></v-col
      >
    </v-row>
    <v-row justify="center">
      <v-col cols="10" class="text-center">
        <p>
          Just fill in the phone number you want to WhatsApp in international
          form e.g. +1 650 555 7475
        </p>
      </v-col>
      <v-col cols="12">
        <v-divider></v-divider>
      </v-col>
      <v-col cols="10" class="text-center">
        Sometimes you want to sent a WhatsApp message without going to the
        trouble of adding someone to your contacts. Or you don't want to bloat
        your contacts list with everyone you ever have sent a WhatsApp message.
        This service is for you.
      </v-col>
    </v-row>
  </v-container>
</template>
<script lang="ts">
import Vue from "vue";
export default Vue.extend({
  transition(to, from) {
    if (!from) {
      return "slide-left";
    }
    return +to.query.page < +from.query.page ? "slide-right" : "slide-left";
  },
  mounted() {
    this.$nextTick(() => {
      this.$nuxt.$loading.start();
      setTimeout(() => this.$nuxt.$loading.finish(), 500);
    });
  },
  name: "WhatsAppMsg",
  methods: {
    routeToWhatsApp() {
      window.location.href = `https://wa.me/${this.phone}`;
    },
  },
  data() {
    return {
      isActive: false,
      phone: "",
    };
  },
});
</script>
