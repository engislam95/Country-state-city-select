# Global Country State City Select

#### Basic library for Country, State and City with select inputs

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://github.com/engislam95/Country-state-city-select)

Basic library for Country, State and City with select inputs built with vue.js.

- Input select with all countries around the world
- Select for states of that country
- Input select with option Cities belong to that state
- Allow to customize it using props

## Installation

CountryStateCitySelect requires [Node.js](https://nodejs.org/) to run.

Install the dependencies and devDependencies and start the server.

```sh
npm i global-country-state-city-select
```

## Props

|                    Props                    |  Type   |                 Default                 |                                                         Description                                                          |
| :-----------------------------------------: | :-----: | :-------------------------------------: | :--------------------------------------------------------------------------------------------------------------------------: | 
|    countryLabel , stateLabel , cityLabel    | String  | Choose your { country , state , city }: |                                            Label to show above the select input.                                             |
| countryBgColor , stateBgColor , cityBgColor | String  |                 default                 |                 Background color of your input select with white text accept option { blue , red , green }.                  |
|     countrySize , stateSize , citySize      | String  |            default { 14px }             | Applying {padding , borderRadius , fontSize , lineHeight } of your input select and accept option {small , default , large } |
| countryRounded , stateRounded , cityRounded | Boolean |            default { True }             |                  Applying { borderRadius of 60px } of your input select and accept option { true , false }                   | 

## Usage Example

```sh
<global-country-state-city-select :countryLabel="new label form country select" :stateBgColor="blue"  :citySize="large" :countryRounded="false" />

```

## How to import it in your vue app

In your main.js, or a similar entry point for your app:

```sh
import SelectCountryStateCity from "SelectCountryStateCity";
```

```sh
import Vue from "vue";
```

```sh
Vue.use(SelectCountryStateCity);
```

## Plugins

CountryStateCitySelect is currently extended with the following plugins.
Instructions on how to use them in your own application are linked below.

| Plugin    | README                             |
| --------- | ---------------------------------- |
| Bili      | [https://bili.egoist.sh][pldb]     |
| Rollup.js | [https://rollupjs.org/guide][plgh] |

## License

MIT
