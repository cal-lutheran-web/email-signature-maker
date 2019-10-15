<template>
	<div class="form-item form-item-inline form-item-img">
		<label :for="this.$vnode.key" :class="{ checked : badge.display }">
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
		padding: .25rem;
	}

	.form-item-img label img {
		opacity: 0.75;
	}

	.form-item-img label.checked {
		background-color: #00854f;
	}

	.form-item-img label.checked img {
		opacity: 1;
	}

	.form-item-img input { display: none; }
</style>