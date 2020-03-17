<template lang="pug">
	div
		span {{ value }}
</template>

<script>
	export default{
		name: 'input-responde-params',
		props: {
			value: {
				type: Number,
				default() {
					return 0
				}
			}
		},
		data(){
			return{

			}
		}
	}
</script>

<style>
</style>