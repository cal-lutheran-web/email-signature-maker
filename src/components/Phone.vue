<template>
	<div class="form-item">
		<label for="phone">{{ phone.label ? formData.phoneTypes[phone.label].shortLabel : 'Enter a phone number' }}</label>
		<select v-model="phone.label" id="phone" class="form-select-small">
			<option value=""></option>
			<option v-for="(phoneType,key) in formData.phoneTypes" :value="key" :key="key">{{ phoneType.label }}</option>
		</select>
		<div class="form-label-prefix">
			<p v-if="phone.label == 'clu_campus'">{{ formData.phoneTypes['clu_campus'].prefix }}</p>
			<p v-if="phone.label == 'plts_campus'">{{ formData.phoneTypes['plts_campus'].prefix }}</p>

			<label class="sr-only" :for="this.$vnode.key"></label>

			<input v-model="phone.number" type="text" :id="this.$vnode.key" v-if="phone.label" :maxlength="this.formData.phoneTypes[this.phone.label].maxLength" :placeholder="this.formData.phoneTypes[this.phone.label].placeholder" />
		</div>
	</div>
</template>

<script>
	export default {
		name: "Phone",
		props: ["formData"],
		watch: {
			phone: {
				handler: "setPhoneData",
				deep: true
			},
			"phone.label": function(data) {
				this.phone.number = "";
			}
		},
		methods: {
			setPhoneData(newData) {
				this.$set(this.formData.phones, this.$vnode.key, {
					number: this.phone.number,
					label: this.phone.label
				});
			}
		},
		data() {
			return {
				phone: {
					number: "",
					label: ""
				}
			};
		}
	};
</script>

<style>
	.form-item .form-select-small {
		width: auto;
	}
</style>