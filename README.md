# Country State City Select
#### Basic library for Country, State and City with select inputs 

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://github.com/engislam95/Country-state-city-select)

Basic library for Country, State and City with select inputs built with vue.js.

- Input select with all countries around the world
- Select for states of that country
- Input select with option Cities belong to that state 

## Installation

CountryStateCitySelect  requires [Node.js](https://nodejs.org/)  to run.

Install the dependencies and devDependencies and start the server.

```sh
cd 'your folder'
npm i
npm install -g @vue/cli
npm install -g @vue/cli-service-global
npm i global-country-state-city-select 
```

## Plugins

CountryStateCitySelect  is currently extended with the following plugins.
Instructions on how to use them in your own application are linked below.

| Plugin | README |
| ------ | ------ |
| Bili | [https://bili.egoist.sh][PlDb] |
| Rollup.js  | [https://rollupjs.org/guide][PlGh] |


#### How to use it 

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

## License

MIT