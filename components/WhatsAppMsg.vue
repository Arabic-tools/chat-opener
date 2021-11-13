<template>
  <v-container >
    <v-row class="py-3">
      <v-col class="text-center">
        <p>Send a WhatsApp direct without adding to your contact list</p>
      </v-col>
    </v-row>
    <v-row justify="center">
      <v-col cols="10" md="6">
        <v-text-field
          solo
          class="inputPrice"
          v-model="phone"
          type="number"
          label="Phone Number"
          :rules="[(v) => !!v || 'Phone number is required']"
          required
        ></v-text-field>
      </v-col>
      <v-col cols="10" class="text-center"
        ><v-btn @click="routeToWhatsApp" color="#00E675" class="white--text"
          >Message now
        </v-btn></v-col
      >
    </v-row>
    <v-row justify="center">
      <v-col cols="10" class="text-center">
        <p>
          Just fill in the phone number you want to WhatsApp in international
          form e.g. +1 650 555 1234
        </p>
        <p>
          Tip: Press enter to open Whatsapp. You may copy & paste the phone
          number, the system will automatically delete unnecessary spaces,
          parenthesizes, and dashes between numbers
        </p>
      </v-col>
    </v-row>

    <v-row class="grey--text text-center">
      <v-col cols="12">
        <v-divider></v-divider>
      </v-col>
      <v-col>
        Do you want to send WhatsApp without saving the number to your contact
        list? How to send a message to an unsaved number in Whatsapp?
        <br />
        Use Chatopener. <br /><br />
        Is Chatopener free?
        <br />Chatopener is free forever.
        <br />
        <br />
        Do you save any data?<br />
        We save no data on our end.
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
  watch: {
    phone() {
      let out = "";
      for (let i of this.phone) {
        console.log(i);
        if (+i > 0 && +i < 9) {
          out += i;
        }
      }
      this.phone = out;
    },
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
      window.open(`https://wa.me/${this.phone}`, "_blank");
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
<style scoped>
.inputPrice >>> input[type="number"] {
  -moz-appearance: textfield;
}
.inputPrice >>> input::-webkit-outer-spin-button,
.inputPrice >>> input::-webkit-inner-spin-button {
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
}
</style>
