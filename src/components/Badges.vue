<template>
	<div class="form-item form-item-img">
		<input :id="this.$vnode.key" v-model="badge.display" type="checkbox" />
		
		<label :for="this.$vnode.key" :class="{ checked : badge.display }">
			<span class="sr-only">{{ badge.name }}</span>
			<img :src="badge.img" width="auto" height="60px" :alt="badge.name" />
		</label>
		
		<aside class="form-item-description">
			<p>{{ badge.description }} <a :href="badge.link" target="_blank">Read More</a></p>
		</aside>
	</div>
</template>

<script>
	export default {
		name: "Badges",
		props: ["badge"]
	};
</script>

<style>
	.form-item-img label {
		cursor: pointer;
		width: 60px;
		margin-right: 1rem;
		margin-left: 1rem;
		flex: 0 0 60px;
		background: white;
		text-align: center;
	}

	.form-item-img {
		display: flex;
		align-items: center;
	}

	.form-item-img label img {
		opacity: 0.75;
		margin: auto;
	}

	.form-item-img label.checked {
		box-shadow: 0 0 0 4px #31b27d;
	}

	.form-item-img label.checked img {
		opacity: 1;
	}

	.form-item-description p {
		padding: 0;
	}
</style>