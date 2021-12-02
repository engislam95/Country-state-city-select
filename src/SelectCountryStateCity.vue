<template>
  <div class="container">
    <link
      rel="stylesheet"
      href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css"
      integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3"
      crossorigin="anonymous"
    />
    <label for="cars">{{ countryLabel }}</label>
    <select
      class="form-select"
      :class="[
        'country-inp-select--' + countryBgColor,
        'country-inp-select--' + countrySize,
        {
          'country-inp-select--rounded': countryRounded,
        },
      ]"
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
    <label for="cars">{{ stateLabel }}</label>
    <select
      class="form-select"
      :class="[
        'state-inp-select--' + stateBgColor,
        'state-inp-select--' + stateSize,
        {
          'state-inp-select--rounded': stateRounded,
        },
      ]"
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
    <label for="cars">{{ cityLabel }}</label>
    <select
      :disabled="selectedState == ''"
      class="form-select"
      :class="[
        'city-inp-select--' + cityBgColor,
        'city-inp-select--' + citySize,
        {
          'city-inp-select--rounded': cityRounded,
        },
      ]"
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
  props: {
    // country
    countryLabel: {
      type: String,
      default: "Choose your country :",
    },
    countryBgColor: {
      type: String,
      default: "default",
      validator(x) {
        return ["default", "blue", "green", "red"].indexOf(x) !== -1;
      },
    },
    countryRounded: {
      type: Boolean,
      default: true,
    },
    countrySize: {
      type: String,
      default: "default",
      validator(x) {
        return ["small", "default", "large"].indexOf(x) !== -1;
      },
    },

    // state
    stateLabel: {
      type: String,
      default: "Choose your state :",
    },
    stateBgColor: {
      type: String,
      default: "default",
      validator(x) {
        return ["default", "blue", "green", "red"].indexOf(x) !== -1;
      },
    },
    stateRounded: {
      type: Boolean,
      default: true,
    },
    stateSize: {
      type: String,
      default: "default",
      validator(x) {
        return ["small", "default", "large"].indexOf(x) !== -1;
      },
    },

    // city
    cityLabel: {
      type: String,
      default: "Choose your city :",
    },
    cityBgColor: {
      type: String,
      default: "default",
      validator(x) {
        return ["default", "blue", "green", "red"].indexOf(x) !== -1;
      },
    },
    cityRounded: {
      type: Boolean,
      default: true,
    },
    citySize: {
      type: String,
      default: "default",
      validator(x) {
        return ["small", "default", "large"].indexOf(x) !== -1;
      },
    },
  },
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

<style >
/* country */
.country-inp-select--blue {
  background-color: #0194ef !important;
  color: #fff !important ;
}

.country-inp-select--green {
  background-color: #1bb934 !important;
  color: #fff !important ;
}

.country-inp-select--red {
  background-color: #e1112c !important;
  color: #fff !important ;
}

/* state */

.state-inp-select--blue {
  background-color: #0194ef !important;
  color: #fff !important ;
}

.state-inp-select--green {
  background-color: #1bb934 !important;
  color: #fff !important ;
}

.state-inp-select--red {
  background-color: #e1112c !important;
  color: #fff !important ;
}

/* city */

.city-inp-select--blue {
  background-color: #0194ef !important;
  color: #fff !important ;
}

.city-inp-select--green {
  background-color: #1bb934 !important;
  color: #fff !important ;
}

.city-inp-select--red {
  background-color: #e1112c !important;
  color: #fff !important ;
}

/* --> SIZES <-- */

/* country */
.country-inp-select--small {
  padding: 8px 10px !important;
  border-radius: 4px !important;
  font-size: 12px !important;
  line-height: 12px !important;
}

.country-inp-select--default {
  padding: 12px 14px !important;
  border-radius: 6px !important;
  font-size: 14px !important;
  line-height: 16px !important;
}

.country-inp-select--large {
  padding: 16px 18px !important;
  border-radius: 8px !important;
  font-size: 16px !important;
  line-height: 20px !important;
}

/* state */

.state-inp-select--small {
  padding: 8px 10px !important;
  border-radius: 4px !important;
  font-size: 12px !important;
  line-height: 12px !important;
}

.state-inp-select--default {
  padding: 12px 14px !important;
  border-radius: 6px !important;
  font-size: 14px !important;
  line-height: 16px !important;
}

.state-inp-select--large {
  padding: 16px 18px !important;
  border-radius: 8px !important;
  font-size: 16px !important;
  line-height: 20px !important;
}

/* city */

.city-inp-select--small {
  padding: 8px 10px !important;
  border-radius: 4px !important;
  font-size: 12px !important;
  line-height: 12px !important;
}

.city-inp-select--default {
  padding: 12px 14px !important;
  border-radius: 6px !important;
  font-size: 14px !important;
  line-height: 16px !important;
}

.city-inp-select--large {
  padding: 16px 18px !important;
  border-radius: 8px !important;
  font-size: 16px !important;
  line-height: 20px !important;
}
/* --> BOOLEANS <-- */

/* country */
.country-inp-select--rounded {
  border-radius: 60px !important;
}
/* state */
.state-inp-select--rounded {
  border-radius: 60px !important;
}
/* city */
.city-inp-select--rounded {
  border-radius: 60px !important;
}
</style>