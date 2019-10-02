<template>
	<div class="row">
		<div class="col-sm-6">
			<FormFields :formData="formData" />
		</div>
		<div class="col-sm-6 sig-area">
			<Sig :formData="formData" />
		</div>
	</div>
</template>


<script>
	import Vue from "vue";
	import FormFields from "./components/FormFields.vue";
	import Sig from "./components/Sig.vue";

	export default {
		data() {
			return {
				formData: {
					name: "",
					title: "",
					department: "",
					mail_code: "",
					phone: "",
					fax: "",
					website: "",
					pronouns_display: "",
					pronouns: "",
					pronouns_custom: "",
					logo: "callutheran",
					logos: {
						callutheran:
							"https://www.callutheran.edu/offices/marketing/brand/images/CLU-default-signature.png",
						som:
							"https://www.callutheran.edu/offices/marketing/brand/images/CLU-som-signature.png",
						coas:
							"https://www.callutheran.edu/offices/marketing/brand/images/CLU-coas-signature.png",
						gsoe:
							"https://www.callutheran.edu/offices/marketing/brand/images/CLU-gsoe-signature.png",
						gsop:
							"https://www.callutheran.edu/offices/marketing/brand/images/CLU-gsop-signature.png",
						pros:
							"https://www.callutheran.edu/offices/marketing/brand/images/CLU-professionals-signature.png",
						plts:
							"https://www.callutheran.edu/offices/marketing/brand/email/images/plts.png"
					},
					social_media_display: false,
					social_media: {
						facebook: "https://www.facebook.com/callutheran",
						instagram: "https://www.instagram.com/callutheran/",
						youtube: "https://youtube.com/callutheran",
						twitter: "https://twitter.com/callutheran"
					}
				}
			};
		},
		components: {
			FormFields,
			Sig
		}
	};
</script>


<style>
	.page-content {
		margin-top: 3rem;
	}

	.sig-area {
		position: sticky;
		top: 25%;
	}
</style>