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
						callutheran:
							"https://www.callutheran.edu/offices/marketing/brand/email/images/cal-lutheran@2x.png",
						som:
							"https://www.callutheran.edu/offices/marketing/brand/email/images/som@2x.png",
						coas:
							"https://www.callutheran.edu/offices/marketing/brand/email/images/coas@2x.png",
						gsoe:
							"https://www.callutheran.edu/offices/marketing/brand/email/images/gsoe@2x.png",
						gsop:
							"https://www.callutheran.edu/offices/marketing/brand/email/images/gsop@2x.png",
						pcs:
							"https://www.callutheran.edu/offices/marketing/brand/email/images/pcs.png",
						plts:
							"https://www.callutheran.edu/offices/marketing/brand/email/images/plts@2x.png",
						sports:
							"https://www.callutheran.edu/offices/marketing/brand/email/images/spirit-mark@2x.png"
					},
					social_media_display: false,
					social_media: {
						facebook: {
							name: "Facebook",
							url: "https://www.facebook.com/callutheran",
							img: "https://www.callutheran.edu/offices/marketing/brand/email/images/facebook.png"
						},
						instagram: {
							name: "Instagram",
							url: "https://www.instagram.com/callutheran/",
							img: "https://www.callutheran.edu/offices/marketing/brand/email/images/instagram.png"
						},
						youtube: {
							name: "YouTube",
							url: "https://youtube.com/callutheran",
							img: "https://www.callutheran.edu/offices/marketing/brand/email/images/youtube.png"
						},
						twitter: {
							name: "Twitter",
							url: "https://twitter.com/callutheran",
							img: "https://www.callutheran.edu/offices/marketing/brand/email/images/twitter.png"
						},
						linkedin: {
							name: "LinkedIn",
							url: "https://www.linkedin.com/school/california-lutheran-university/",
							img: "https://www.callutheran.edu/offices/marketing/brand/email/images/linkedin.png"
						}
					},
					phoneTypes: {
						clu_campus: {
							label: "Cal Lutheran Extension",
							shortLabel: "Office",
							prefix: "(805) 493-",
							maxLength: "4",
							placeholder: "xxxx"
						},
						plts_campus: {
							label: "PLTS Campus Extension",
							shortLabel: "Office",
							prefix: "(510) 559-",
							maxLength: "4",
							placeholder: "xxxx"
						},
						fax: {
							label: "Fax",
							shortLabel: "Fax",
							prefix: "",
							maxLength: "",
							placeholder: "(xxx) xxx-xxxx"
						},
						mobile: {
							label: "Mobile",
							shortLabel: "Mobile",
							prefix: "",
							maxLength: "",
							placeholder: "(xxx) xxx-xxxx"
						}
					},
					badges_display: false,
					badges: {
						bridge: {
							img:
								"https://www.callutheran.edu/offices/marketing/brand/email/images/BRIDGE.png",
							name: "BRIDGE",
							description: "BRIDGE Ally trainings help build regular interfaith dialogue on campus.",
							link: "https://www.callutheran.edu/mission-identity/bridge.html"
						},
						dreamer: {
							img:
								"https://www.callutheran.edu/offices/marketing/brand/email/images/DREAMer-Ally.png",
							name: "DREAMer Ally",
							description: "DREAMer Ally Training creates a network of support for undocumented/DACAmented students or students who come from a mixed status family.",
							link: "https://www.callutheran.edu/admission/undergraduate/dream-act/dreamer-ally/index.html"
						},
						vetnet: {
							img:
								"https://www.callutheran.edu/offices/marketing/brand/email/images/VET-NET-ALLY.png",
							name: "VET NET Ally",
							description: "VET NET Ally trainings create a welcoming and supportive campus environment for military services members and veterans.",
							link: "https://www.callutheran.edu/veterans/resources/vet-net-ally.html"
						},
						safe_zone: {
							img:
								"https://www.callutheran.edu/offices/marketing/brand/email/images/Safe-Zone.png",
							name: "Safe Zone",
							description: "Safe Zone Ally trainings create an atmosphere of support for the LGBTQIA community on campus.",
							link: "https://www.callutheran.edu/students/counseling/safe-zone.html"
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