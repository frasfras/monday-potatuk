<template>
  <div class="about">
    <HelloWorld />
    <div class="container-fluid">
      <div class="row-fluid">
        <div class="span12"></div>
      </div>
      <v-row>
        <v-col cols="4" sm="6" md="6">
          <div class="span5 well"></div>
        </v-col>
        <v-col class="span7"> </v-col>
      </v-row>
    </div>
    <h2 class="headline font-weight-bold mb-3"></h2>

    <v-row justify="center">
      <a
        v-for="(eco, i) in ecosystem"
        :key="i"
        :href="eco.href"
        class="subheading mx-3"
        target="_blank"
      >
        {{ eco.text }}
      </a>
    </v-row>
  </div>
</template>

<script>
import HelloWorld from "../components/VolunteerOpp";

export default {
  name: "HomeView",

  components: {
    HelloWorld,
  },
  data: () => ({
    ecosystem: [
      {
        text: "ecologi",
        href: "https://ecologi.com/",
      },
      {
        text: "github",
        href: "https://notreaffaireatous.org/",
      },
    ],
    valid: false,
    itemname: "",
    description: "",
    url: "",
    checkbox: true,
    checkbox2: true,
    items: [
      "Multinationals hack",
      "RIGHTS OF NATURE",
      "ecocide",
      "De education",
      "De Climatologist",
      "Biodiversity",
    ],
    fx9: { label: "Reserved hours", val: 50, color: "#234560" },
    nameRules: [
      (v) => !!v || "Name is required",
      (v) => v.length <= 10 || "Name must be less than 10 characters",
    ],
  }),
};
</script>
