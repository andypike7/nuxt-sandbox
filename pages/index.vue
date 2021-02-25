<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6" class="text-center">
      Hello, {{ fullName }}!<br />
      Or {{ doubleName }}!<br />
      Host: '{{ localHost }}'<br />
      NavigationLink:
      <NavigationLink url="/profile">
        Профиль
        <template v-slot:payload></template>
      </NavigationLink>
      <v-text-field
        v-model="firstName"
        :rules="rules"
        :counter="nameLimit"
        hint="This field uses counter prop"
        label="First Name"
      />
      <v-text-field
        v-model="lastName"
        :rules="rules"
        :counter="nameLimit"
        hint="This field uses counter prop"
        label="Last Name"
      />
      <v-select
        v-model="age"
        label="Your age"
        placeholder="Select..."
        :items="ages"
        mandatory="0"
      />
      <v-radio-group v-model="sex" label="Your sex" row>
        <!-- <v-radio label="Doesn't matter" value="0" /> -->
        <v-radio label="Male" value="1" />
        <v-radio label="Female" value="2" />
        <v-radio label="Don't know" value="3" />
      </v-radio-group>
      <v-file-input placeholder="Upload a photo..." />
      <!-- <div class="text-center">
        <logo />
        <vuetify-logo />
      </div>
      0<v-card>
        <v-card-title class="headline">
          Welcome to the Vuetify + Nuxt.js template
        </v-card-title>
        <v-card-text>
          <p>
            Vuetify is a progressive Material Design component framework for
            Vue.js. It was designed to empower developers to create amazing
            applications.
          </p>
          <p>
            For more information on Vuetify, check out the
            <a
              href="https://vuetifyjs.com"
              target="_blank"
              rel="noopener noreferrer"
            >
              documentation </a
            >.
          </p>
          <p>
            If you have questions, please join the official
            <a
              href="https://chat.vuetifyjs.com/"
              target="_blank"
              rel="noopener noreferrer"
              title="chat"
            >
              discord </a
            >.
          </p>
          <p>
            Find a bug? Report it on the github
            <a
              href="https://github.com/vuetifyjs/vuetify/issues"
              target="_blank"
              rel="noopener noreferrer"
              title="contribute"
            >
              issue board </a
            >.
          </p>
          <p>
            Thank you for developing with Vuetify and I look forward to bringing
            more exciting features in the future.
          </p>
          <div class="text-xs-right">
            <em><small>&mdash; John Leider</small></em>
          </div>
          <hr class="my-3" />
          <a
            href="https://nuxtjs.org/"
            target="_blank"
            rel="noopener noreferrer"
          >
            Nuxt Documentation
          </a>
          <br />
          <a
            href="https://github.com/nuxt/nuxt.js"
            target="_blank"
            rel="noopener noreferrer"
          >
            Nuxt GitHub
          </a>
        </v-card-text>
        <v-card-actions>
          <v-spacer />
          <v-btn color="primary" nuxt to="/inspire"> Continue </v-btn>
        </v-card-actions>
      </v-card> -->
    </v-col>
  </v-row>
</template>

<script>
// import Logo from '~/components/Logo.vue'
// import VuetifyLogo from '~/components/VuetifyLogo.vue'
import Vue from 'vue';
import Config from '@/components/constants';
import NavigationLink from '@/components/NavigationLink';

const NAME_LIMIT = 25;
const AGE_FROM = 16;
const AGE_TO = 50;

export default {
  components: {
    // Logo,
    // VuetifyLogo,
    NavigationLink,
  },
  data() {
    return {
      firstName: 'Ivan',
      lastName: 'Ivanov',
      rules: [],
      nameLimit: NAME_LIMIT,
      sex: '0',
      age: '0',
      ages: [],
      localHost: Config.host,
    };
  },
  computed: {
    fullName() {
      console.log('*** Vue.version:', Vue.version);
      return this.firstName.trim().length === 0 &&
        this.lastName.trim().length === 0
        ? 'user'
        : `${this.firstName} ${this.lastName}`;
    },
    doubleName() {
      return this.fullName + ' | ' + this.fullName;
    },
  },
  mounted() {
    this.ages.push(`It doesn't matter`);
    this.ages.push(`Less than ${AGE_FROM}`);
    for (let i = AGE_FROM; i < AGE_TO; i++) {
      this.ages.push(`I'm ${i}`);
    }
    this.ages.push(`More than ${AGE_TO}`);
    this.ages.push('I forgot');
  },
};
</script>
