<template>
	<div class="form-item form-item-inline form-item-img">
		<label :for="this.$vnode.key">
			<span class="sr-only">{{ badge.name }}</span>
			<img :src="badge.img" width="60px" height="auto" />
		</label>
		<input :id="this.$vnode.key" v-model="badge.display" type="checkbox" />
		
	</div>
</template>

<script>
export default {
	name: "Badges",
	props: ["badge"]
}
</script>

<style>
	.form-item-img label {
		cursor: pointer;
	}
</style>