<template>

      <v-container>
        <v-row>
          <v-col>
            <v-text-field
              solo-inverted
              v-model="phone"
              type="number"
              label="Phone Number"
              counter="14"
              :rules="[(v) => !!v || 'Phone number is required']"
              required
            ></v-text-field>
          </v-col>
        </v-row>
        <v-row>
          <v-col><v-btn @click="routeToWhatsApp">hello</v-btn></v-col>
        </v-row>
      </v-container>

</template>
<script lang="ts">
import Vue from "vue";
export default Vue.extend({
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
