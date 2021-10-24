<template>
  <div class="container">
    <link
      rel="stylesheet"
      href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css"
      integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3"
      crossorigin="anonymous"
    />
    <label for="cars">Choose your country :</label>
    <select
      class="form-select"
      aria-label="Default select country"
      v-model="selectedCountry"
      @change="fireState()"
    >
      <option selected hidden>Open this select menu</option>
      <option
        :value="country.id"
        v-for="country in countries"
        :key="country.id"
      >
        {{ country.name }}
      </option>
    </select>
    <label for="cars">Choose your state :</label>
    <select
      class="form-select"
      :disabled="selectedCountry == ''"
      aria-label="Default select country"
      v-model="selectedState"
      @change="fireCity()"
    >
      <option hidden selected>Open this select menu</option>
      <option :value="state.id" v-for="state in states" :key="state.id">
        {{ state.name }}
      </option>
    </select>
    <label for="cars">Choose your city :</label>
    <select
    :disabled="selectedState == ''"
      class="form-select"
      aria-label="Default select country"
      v-model="selectedCity"
    >
      <option hidden selected>Open this select menu</option>
      <option :value="city.id" v-for="city in cities" :key="city.id">
        {{ city.name }}
      </option>
    </select>
  </div>
</template>

<script>
import listCountries from "./json/country.json";
import listStates from "./json/state.json";
import listCities from "./json/city.json";

export default {
  data() {
    return {
      countries: listCountries,
      selectedCountry: "",
      selectedState: "",
      selectedCity: "",
      states: [],
      cities: [],
    };
  },
  mounted() {},
  methods: {
    fireState() {
      this.states = [];
      listStates.map((state) => {
        if (state.country_id == this.selectedCountry) {
          this.states.push(state);
        } else {
          this.arrayRemove(this.states, state);
        }
      });
    },
    fireCity() {
      this.cities = [];
      listCities.map((city) => {
        if (city.state_id == this.selectedState) {
          this.cities.push(city);
        } else {
          this.arrayRemove(this.cities, city);
        }
      });
    },
    arrayRemove(arr, value) {
      return arr.filter(function (ele) {
        return ele != value;
      });
    },
  },
};
</script>

