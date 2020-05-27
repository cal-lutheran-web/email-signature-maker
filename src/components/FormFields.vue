<template>
	<form class="form-fields">
		<fieldset name="basic-info">
			<legend><span>Basic Info</span></legend>

			<div class="form-item">
				<label for="name">Name</label>
				<input v-model="formData.name" id="name" type="text" />
			</div>

			<div class="form-item">
				<label for="title">Title</label>
				<input v-model="formData.title" id="title" type="text" />
			</div>

			<div class="form-item">
				<label for="pronouns">Pronouns</label>
				<select id="pronouns" v-model="formData.pronouns">
					<option></option>
					<option value="He/Him/His">He/Him/His</option>
					<option value="She/Her/Hers">She/Her/Hers</option>
					<option value="They/Them/Theirs">They/Them/Theirs</option>
					<option value="custom">Custom</option>
				</select>
				<p><a href="https://www.callutheran.edu/offices/marketing/brand/email/gender-pronouns.html" class="fancy">Learn more about gender pronouns</a></p>
			</div>

			<div class="form-item" v-if="formData.pronouns == 'custom'">
				<label for="pronouns-custom">Custom Pronouns</label>
				<input v-model="formData.pronouns_custom" id="pronouns-custom" type="text" />
			</div>

		</fieldset>


		<fieldset name="department-info">
			<legend><span>Department Info</span></legend>

			<div class="form-item">
				<label for="logo">School Mark</label>
				<select v-model="formData.logo" id="logo">
					<option value="callutheran" selected="true">Cal Lutheran</option>
					<option value="coas">College of Arts &amp; Sciences</option>
					<option value="som">School of Management</option>
					<option value="gsoe">Graduate School of Education</option>
					<option value="gsop">Graduate School of Psychology</option>
					<option value="pcs">School for Professional and Continuing Studies</option>
					<option value="plts">Pacific Lutheran Theological Seminary</option>
					<option value="sports">Spirit Mark (Athletics-use only)</option>
				</select>
			</div>

			<div class="form-item">
				<label for="department">Department</label>
				<input v-model="formData.department" id="department" type="text" />
			</div>

			<div class="form-item">
				<label for="website">Website</label>
				<div class="form-label-prefix">
					<p v-if="formData.logo !== 'plts'">CalLutheran.edu/</p>
					<p v-if="formData.logo == 'plts'">PLTS.edu/</p> 
					<input v-model="formData.website" id="website" type="text" />
				</div>
			</div>

		</fieldset>

		<fieldset name="contact-info">
			<legend><span>Contact Info</span></legend>
		
			<div class="form-item">
				<label for="mail_code">Mail Code</label>
				<input v-model="formData.mail_code" id="mail_code" type="text" />
			</div>

			<Phone :formData="formData" key="phone_1"></Phone>
			<Phone :formData="formData" key="phone_2"></Phone>
			<Phone :formData="formData" key="phone_3"></Phone>

		</fieldset>

		<fieldset name="social-media-info">
			<legend>Social Media Info</legend>

			<div class="form-item form-item-inline">
				<label for="social-media">Show Social Media Icons</label>
				<input id="social-media" type="checkbox" v-model="formData.social_media_display" />
			</div>

			<template v-for="(sm, key) in formData.social_media">
				<div class="form-item" v-if="formData.social_media_display" :key="key">
					<label :for="key">{{ sm.name }}</label>
					<input v-model="sm.url" :id="key" type="text" />
				</div>
			</template>


		</fieldset>

		<fieldset name="badges-info">
			<legend>Badges</legend>

			<p>To continue serving and meeting our students’ needs, Cal Lutheran faculty and staff members can receive training to become official allies for some of our most vulnerable students.</p>

			<p>Have you received campus ally training?</p>

			<div class="form-item">
				<label for="badges-toggle-yes">Yes</label> <input v-model="formData.badges_display" id="badges-toggle-yes" type="radio" value="true" />
			</div>

			<div class="form-item">
				<label for="badges-toggle-no">No</label> <input v-model="formData.badges_display" id="badges-toggle-no" type="radio" value="false" />
			</div>

			<div class="badges" >
				<template v-for="(badge,key) in formData.badges">
					<Badges :badge="badge" :disabled="formData.badges_display" :key="key"></Badges>
				</template>
			</div>

		</fieldset>
		
	</form>
</template>

<script>
	import Vue from "vue";
	import Phone from "./Phone.vue";
	import Badges from "./Badges.vue";

	export default {
		name: "FormFields",
		props: ["formData"],
		components: {
			Phone,
			Badges
		},
		data() {
			return {
				social_media_display: false
			};
		},
		watch: {
			"formData.pronouns": function(data) {
				if (data == "custom") {
					this.formData.pronouns_display = this.formData.pronouns_custom;
				} else {
					this.formData.pronouns_display = data;
				}
			},
			"formData.pronouns_custom": function(data) {
				this.formData.pronouns_display = data;
			}
		}
	};
</script>

<style>
	.form-item {
		margin-bottom: 1rem;
	}

	.form-item label {
		display: block;
	}

	.form-item select,
	.form-item input[type="text"] {
		width: 100%;
	}

	.form-item-inline {
		display: flex;
	}

	.form-item-inline label {
		display: inline-block;
		margin-left: 1ch;
		order: 2;
	}

	.form-label-prefix {
		display: flex;
		align-items: center;
	}
	.form-label-prefix p {
		padding: 0 1ch 0 0;
		flex: 0 0 auto;
	}

	fieldset {
		border: 0;
		margin: 0 0 2rem 0;
		padding: 1rem;
		position: static;
		background-color: #aadff1;
	}

	fieldset h3 {
		color: #333;
		font-family: Raleway, sans-serif;
		font-size: 1rem;
		line-height: 1.5em;
		margin: 0;
		letter-spacing: normal;
		font-weight: bold;
	}

	legend {
		display: block;
		box-sizing: content-box;
		position: static;
		width: 100%;
		margin: 0 -1rem;
		font-family: "Tungsten", Impact, sans-serif;
		font-size: 30px;
		color: white;
		background: #1e5989;
		padding: 0.5rem 1rem;
		font-weight: normal;
	}

	legend span {
		display: block;
	}

	.form-flex {
		display: flex;
	}
</style>