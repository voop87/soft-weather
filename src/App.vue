<template>
	<h1>
		Прогноз погоды <span v-if="!errored" class="town-name">{{ town }}</span>
	</h1>
	<hr>
	<SearchTown @search="searchTown"/>
	<WeatherTable
		:forecast='forecast'
		v-if="forecast.length > 0"
	/>
	<p class="fs-2" v-if="errored">Упс, ничего не найдено! Попробуйте ввести другой город..</p>
</template>

<script>
import SearchTown from '@/components/SearchTown'
import WeatherTable from '@/components/WeatherTable'
export default {
  name: 'App',
	data() {
		return {
			town: '',
			forecast: [],
			errored: false
		}
	},
  components: {
		SearchTown,
		WeatherTable
  },
	methods: {
		async searchTown(searchText) {
			this.town = searchText;

			await fetch(`http://api.openweathermap.org/data/2.5/forecast?q=${searchText}&units=metric&cnt=10&appid=63623439096e87e393efaaa735fcb9cd`)
			.then(res => {
				if (res.status === 200 || res.status === 201) {
					this.errored = false;
					res.json()
					.then(json => this.forecast = json.list);
				} else {
					console.log (res.status);
					this.errored = true;
					this.forecast = [];
					return;
				}
			})
		}
	}
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.town-name {
	display: block;
	text-transform: uppercase;
}
</style>
