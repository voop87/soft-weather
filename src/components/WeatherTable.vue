<template>
	<div class="container">
		<table class="table table-dark table-striped">
				<TableHead />
			<tbody>
				<DailyForecast
					v-for="weather in forecast"
					:key="weather.dt"
					:weather="weather"
				/>
			</tbody>
		</table>
	</div>
</template>

<script>
	import TableHead from '@/components/TableHead'
	import DailyForecast from '@/components/DailyForecast'
	export default {
		props: ['forecast'],
		components: {
			TableHead,
			DailyForecast
		}
	}
</script>
