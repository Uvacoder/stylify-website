<template>
	<div
		:class="[
			isBlue ? 'border-color:$blue1 background:lighten($blue3,20)' : '',
			isOrange ? 'border-color:$orange1 color:#000 background:lighten($orange1,30)' : '',
			'note border-left-width:8px border-left-style:solid padding:8px lg:padding:12px'
		]">
		<slot></slot>
	</div>
</template>

<script>
export default {
	props: {
		color: {
			type: String,
			default: 'blue'
		},
		classes: {
			type: String,
			default: null
		}
	},
	computed: {
		isBlue() {
			return this.color === 'blue';
		},
		isOrange() {
			return this.color === 'orange';
		},
	}
}
</script>
