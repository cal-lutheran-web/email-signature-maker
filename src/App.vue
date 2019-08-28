<template>
	
	<div class="container page-content">
		<header class="row">
			<div class="col-sm-12">
				<h1 class="section-title">Email Signature Maker</h1>
			</div>
		</header>
		<div class="row">
			<div class="col-sm-6">
				<div class="form-item">
					<label for="name">Name</label>
					<input v-model="name" type="text" required />
				</div>

				<div class="form-item">
					<label for="title">Title</label>
					<input v-model="title" type="text" required />
				</div>

				<div class="form-item">
					<label for="department">Department</label>
					<input v-model="department" type="text" />
				</div>

				<div class="form-item">
					<label for="mail_code">Mail Code</label>
					<input v-model="mail_code" type="text" />
				</div>

				<div class="form-item">
					<label for="phone">Phone</label>
					<input v-model="phone" type="text" />
				</div>

				<div class="form-item">
					<label for="fax">Fax</label>
					<input v-model="fax" type="text" />
				</div>
			</div>
			<div class="col-sm-6">

				<p style="padding: 0; font-size: 12px; line-height: 15px; font-family: Verdana; color: #3b2360; margin: 0 0 15px 0;">
					<b>{{ name }}</b><br>
					<i>{{ title }}<br>
					<span v-if="department">{{ department }}</span></i>
				</p>
				<img src="https://www.callutheran.edu/offices/marketing/brand/images/CLU-default-signature.png" alt="California Lutheran University" width="250" height="24">
				<p style="padding: 0; font-size: 10px; line-height: 14px; font-family: Verdana; color: #777777; margin: 8px 0 0 0;">
					60 West Olsen Road #{{ mail_code }} &nbsp;|&nbsp; Thousand Oaks, CA 91360<br>
					<span v-if="phone">Phone: (805) 493-{{ phone }} </span><span v-if="fax">&nbsp;|&nbsp; Fax: (805) 493-{{ fax }}</span><br>
					<a href="https://www.callutheran.edu">CalLutheran.edu</a>
				</p>

			</div>
		</div>
	</div>

</template>


<script>

import Vue from "vue";

export default {
	data(){
		return {
			name: 'First Last',
			title: 'Title',
			department: 'Department (optional)',
			mail_code: 'XXXX',
			phone: 'XXXX',
			fax: 'XXXX'
		}
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