<template>
	<tr>
		<td>{{ weather.dt_txt }}</td>
		<td>{{ weather.main.temp }}</td>
		<td>{{ weather.weather[0].description }}</td>
		<td>{{ weather.wind.speed }}</td>
	</tr>
</template>

<script>
export default {
	props: {
		weather: {
			type: Object,
			required: true
		}
	}

}
</script>
