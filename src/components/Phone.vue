<template>
	<div class="form-item">
		<select v-model="phone.label" class="form-select-small">
			<option value=""></option>
			<option v-for="(phoneType,key) in formData.phoneTypes" :value="key" :key="key">{{ phoneType.label }}</option>
		</select>
		<label for="phone" class="sr-only">{{ phone.label ? phone.label : 'Phone Number Type Not Selected' }}</label>
		<div class="form-label-prefix">
			<p v-if="phone.label == 'clu_campus'">805-493-</p>
			<p v-if="phone.label == 'plts_campus'">510-559-</p>
		
			<input v-model="phone.number" type="text" maxlength="4" />
		</div>
	</div>
</template>

<script>
export default {
	name: 'Phone',
	props: ['formData'],
	watch: {
		'phone': {
			handler: 'setPhoneData',
			deep: true
		}
	},
	methods: {
		setPhoneData(newData){
			this.$set(this.formData.phones,this.$vnode.key,{
				'number': this.phone.number,
				'label': this.phone.label
			});
		}
	},
	data(){
		return {
			phone: {
				number: '',
				label: ''
			}
		}
	}
}
</script>

<style>
	.form-item .form-select-small {
		width: auto;
	}
</style>