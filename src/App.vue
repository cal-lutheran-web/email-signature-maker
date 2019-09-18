<template>
	
	<div class="container page-content">
		<header class="row">
			<div class="col-sm-12">
				<h1 class="section-title">Email Signature Maker</h1>
			</div>
		</header>
		<div class="row">
			<div class="col-sm-6">
				<FormFields :formData="formData" />
			</div>
			<div class="col-sm-6">

				<Sig :formData="formData" />

			</div>
		</div>
	</div>

</template>


<script>

import Vue from "vue";
import FormFields from "./components/FormFields.vue";
import Sig from "./components/Sig.vue";

export default {
	data(){
		return {
			formData: {
				name: 'First Last',
				title: 'Title',
				department: 'Department (optional)',
				mail_code: 'XXXX',
				phone: 'XXXX',
				fax: 'XXXX'
			}
		}
	},
	components: {
		FormFields,
		Sig
	}
}

</script>


<style>
	.page-content {
		margin-top: 3rem;
	}

	.form-item {
		margin-bottom: 1rem;
	}

</style>