<template>
  <main>
    <h2>
      Random Names
      <button @click.prevent.stop="roll">
        Reroll
      </button>
    </h2>
    <br>
    <p>{{ data.firstname }} {{ data.middlename }} {{ data.lastname }}</p>
    <p v-text="data.jobtitle" />
    <p v-text="data.email" />
    <p v-text="data.address1" />
    <p v-text="data.address2" />
    <p>{{ data.city }} {{ data.state }}, {{ data.zipcode }}</p>
  </main>
</template>

<script lang="ts">
import Vue from 'vue'
import { faker } from '@faker-js/faker'

export default Vue.extend({
  name: 'IndexPage',
  data (): any {
    return {
      data: {},
    }
  },
  mounted () {
    this.roll()
  },
  methods: {
    roll () {
      const state = faker.address.stateAbbr()
      this.data = {
        firstname: faker.name.firstName(),
        middlename: faker.name.middleName().toUpperCase(),
        lastname: faker.name.lastName(),
        jobtitle: faker.name.jobTitle(),
        email: faker.internet.email(),
        address1: faker.address.streetAddress(),
        address2: faker.address.secondaryAddress(),
        city: faker.address.city(),
        zipcode: faker.address.zipCodeByState(state),
        state,
      }
    },
  },
})
</script>

<style>
body, * {
  color: grey;
  background-color: black;
}
</style>
