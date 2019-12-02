<template>
	<div class="signature-wrapper">
		<div id="signature-content" class="sig" @click="toClipboard">

			<p style="padding: 0; font-size: 12px; line-height: 15px; font-family: Verdana; color: #3b2360; margin: 0 0 15px 0;">
				<b>{{ formData.name ? formData.name : "First Last" }}</b>
				<br />
				<i>
					{{ formData.title ? formData.title : "Title" }}
					<template v-if="formData.department"><br />{{ formData.department }}</template>
					<template v-if="formData.pronouns"><br />Pronouns: {{ formData.pronouns_display }}</template>
				</i>
				
			</p>

			<img
				:src="formData.logos[formData.logo]"
				alt="California Lutheran University"
				:width="this.logo_w ? this.logo_w : 250"
				:height="this.logo_h ? this.logo_h : 24"
				v-if="formData.logo !== 'plts'"
			/>
			
			<img
				:src="formData.logos.plts"
				alt="Pacific Lutheran Theological Seminary"
				:width="this.logo_w ? this.logo_w : 250"
				:height="this.logo_h ? this.logo_h : 24"
				v-if="formData.logo == 'plts'"
			/>

			<p style="padding: 0; font-size: 10px; line-height: 14px; font-family: Verdana; color: #777777; margin: 8px 0 0 0;" >
				<template v-if="formData.logo == 'plts'">
					2000 Center Street, Suite 200 Berkeley, CA 94704
				</template>

				<template v-else>
					60 West Olsen Road <template v-if="formData.mail_code">#{{ formData.mail_code }}</template>&nbsp;|&nbsp;Thousand Oaks, CA 91360
				</template>

				<template v-for="(phone, key, index) in formData.phones">
					<template v-if="index == 0"><br :key="key" /></template>
					<template v-if="index > 0">&nbsp;|&nbsp;</template>
					<template v-if="phone.label">
						{{ formData.phoneTypes[phone.label].shortLabel }}: {{ formData.phoneTypes[phone.label].prefix + phone.number }}
					</template>
				</template>

				<br />

				<a :href="'https://www.callutheran.edu/' + formData.website" v-if="formData.logo !=='plts'">CalLutheran.edu{{ formData.website ? '/'+formData.website : '' }}</a>
				<a :href="'https://www.plts.edu/' + formData.website" v-if="formData.logo == 'plts'">PLTS.edu{{ formData.website ? '/'+formData.website : '' }}</a>
			</p>

			<p v-if="formData.social_media_display" style="margin-top: 1em">
				<a :href="formData.social_media.facebook" v-if="formData.social_media.facebook">
					<img src="https://www.callutheran.edu/offices/marketing/brand/email/images/facebook.png" width="24" height="24" />
				</a>
				<a :href="formData.social_media.instagram" v-if="formData.social_media.instagram">
					<img src="https://www.callutheran.edu/offices/marketing/brand/email/images/instagram.png" width="24" height="24" />
				</a>
				<a :href="formData.social_media.twitter" v-if="formData.social_media.twitter">
					<img src="https://www.callutheran.edu/offices/marketing/brand/email/images/twitter.png" width="24" height="24" />
				</a>
				<a :href="formData.social_media.youtube" v-if="formData.social_media.youtube">
					<img src="https://www.callutheran.edu/offices/marketing/brand/email/images/youtube.png" width="24" height="24" />
				</a>
			</p>

			<p style="margin-top: 1em">
				<template v-for="(badge,key) in formData.badges">
					<img v-if="badge.display" :src="badge.img" width="60" height="60" :key="key" :alt="badge.name" />
				</template>
			</p>
		</div>

		<button @click="toClipboard" class="btn btn-small green">Copy Signature to Clipboard</button>

		<div class="bg-box bg-silver"><p>After copying your signature to the clipboard, open your email signature settings and paste your new signature. Officially supported email clients are Outlook for Windows/MacOS and Outlook Web App. Please contact the Help Desk if you need additional support in adding your signature.</p></div>

		<p v-if="this.confirmCopy">Copied to Clipboard</p>
	</div>
</template>

<style>
	.sig {
		padding: 2rem;
		margin-bottom: 1rem;
		border: 1px solid #bfc5c9;
		position: relative;
	}

	.sig::before {
		content: "Signature Preview";
		display: inline-block;
		background: #bfc5c9;
		color: white;
		font-weight: bold;
		padding: 0.25rem;
		line-height: 1;
		position: absolute;
		top: calc(-1em + -0.5rem + -1px);
		left: -1px;
	}

	.btn {
		margin-bottom: 1rem;
	}
</style>

<script>
	import Vue from "vue";

	export default {
		name: "Sig",
		props: ["formData"],
		data() {
			return {
				logo_w: "",
				logo_h: "",
				confirmCopy: false
			};
		},
		watch: {
			"formData.logo": function(data) {
				var $this = this;
				var img = new Image();
				img.src = this.formData.logos[this.formData.logo];
				img.onload = function() {
					$this.logo_w = this.width / 2;
					$this.logo_h = this.height / 2;
				};
			}
		},
		methods: {
			toClipboard() {
				var sigArea = document.querySelector("#signature-content")
					.innerHTML;

				function listener(e) {
					e.clipboardData.setData("text/html", sigArea);
					e.clipboardData.setData("text/plain", sigArea);
					e.preventDefault();
				}
				document.addEventListener("copy", listener);
				document.execCommand("copy");
				document.removeEventListener("copy", listener);

				this.confirmCopy = true;
			}
		}
	};
</script>