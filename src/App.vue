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
					website: "",
					phones: {},
					pronouns_display: "",
					pronouns: "",
					pronouns_custom: "",
					logo: "callutheran",
					logos: {
						callutheran: "https://www.callutheran.edu/offices/marketing/brand/images/CLU-default-signature.png",
						som: "https://www.callutheran.edu/offices/marketing/brand/images/CLU-som-signature.png",
						coas: "https://www.callutheran.edu/offices/marketing/brand/images/CLU-coas-signature.png",
						gsoe: "https://www.callutheran.edu/offices/marketing/brand/images/CLU-gsoe-signature.png",
						gsop: "https://www.callutheran.edu/offices/marketing/brand/images/CLU-gsop-signature.png",
						pros: "https://www.callutheran.edu/offices/marketing/brand/images/CLU-professionals-signature.png",
						plts: "https://www.callutheran.edu/offices/marketing/brand/email/images/plts.png",
						sports: "https://www.callutheran.edu/offices/marketing/brand/email/images/spirit-mark.png"
					},
					social_media_display: false,
					social_media: {
						facebook: "https://www.facebook.com/callutheran",
						instagram: "https://www.instagram.com/callutheran/",
						youtube: "https://youtube.com/callutheran",
						twitter: "https://twitter.com/callutheran"
					},
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
					badges_display: false,
					badges: {
						bridge: {
							img: "https://www.callutheran.edu/offices/marketing/brand/email/images/BRIDGE.png",
							name: "BRIDGE"
						},
						dreamer: {
							img: "https://www.callutheran.edu/offices/marketing/brand/email/images/DREAMer-Ally.png",
							name: "DREAMer Ally"
						},
						safe_zone: {
							img: "https://www.callutheran.edu/offices/marketing/brand/email/images/Safe-Zone.png",
							name: "Safe Zone"
						},
						vetnet: {
							img: "https://www.callutheran.edu/offices/marketing/brand/email/images/VET-NET-ALLY.png",
							name: "VET NET Ally"
						}
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

	.sr-only {
		border: 0;
		clip: rect(1px, 1px, 1px, 1px);
		clip-path: inset(50%);
		height: 1px;
		margin: -1px;
		overflow: hidden;
		padding: 0;
		position: absolute !important;
		width: 1px;
		word-wrap: normal !important;
	}
</style>