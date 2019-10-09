<template>
	<div class="form-item">
		<select v-model="changeLabel" class="form-select-small">
			<option value=""></option>
			<option v-for="(key,label) in phoneTypes" :value="label" :key="label">{{ key }}</option>
		</select>
		<label for="phone" class="sr-only">{{ label }}</label>
		<div class="form-label-prefix">
			<p v-if="selectedLabel == 'clu_campus'">805-493-</p>
			<p v-if="selectedLabel == 'plts_campus'">510-559-</p>
		
			<input v-model="phoneNumber" type="text" maxlength="4" />
		</div>
	</div>
</template>

<script>
export default {
	name: 'Phone',
	props: ['formData'],
	watch: {
		'phoneNumber': function(newData){
			this.$set(this.formData,this.$vnode.key,{
				'number': newData,
				'label': this.selectedLabel,
				'shortLabel': this.phoneTypes[this.selectedLabel].shortLabel,
				'prefix': this.phoneTypes[this.selectedLabel].prefix
			});
		}
	},
	computed: {
		changeLabel: {
			get(newData){
				return this.selectedLabel;
			},
			set(newData){
				console.log(this.$vnode.key,newData);
				this.selectedLabel = newData;
			}
		}
	},
	data(){
		return {
			phoneTypes: {
				clu_campus: {
					label: 'Cal Lutheran Extension',
					shortLabel: 'Office',
					prefix: '805-493-'
				},
				plts_campus: {
					label: 'PLTS Campus Extension',
					shortLabel: 'Office',
					prefix: '510-559-'
				},
				fax: {
					label: 'Fax',
					shortLabel: 'Fax',
					prefix: ''
				},
				mobile: {
					label: 'Mobile',
					shortLabel: 'Mobile',
					prefix: ''
				}
			},
			phoneNumber: '',
			selectedLabel: ''
		}
	}
}
</script>

<style>
	.form-item .form-select-small {
		width: auto;
	}
</style>