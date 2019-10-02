<template>
	<div class="sig">
		<p style="padding: 0; font-size: 12px; line-height: 15px; font-family: Verdana; color: #3b2360; margin: 0 0 15px 0;">
			<b>{{ formData.name ? formData.name : "First Last" }}</b>
			<br />
			<i>
				{{ formData.title ? formData.title : "Title" }}
				<br />
				<span v-if="formData.department">{{
					formData.department
				}}<br /></span>
				<span v-if="formData.pronouns">
					Pronouns: 
					{{ formData.pronouns_display }}
					<br />
				</span>
			</i>
			
		</p>


		<img
			:src="formData.logos[formData.logo]"
			alt="California Lutheran University"
			width="250"
			:height="this.logo_h ? this.logo_h : 24"
			v-if="formData.logo !== 'plts'"
		/>
		
		<img
			:src="formData.logos.plts"
			alt="Pacific Lutheran Theological Seminary"
			width="250"
			:height="this.logo_h ? this.logo_h : 24"
			v-if="formData.logo == 'plts'"
		/>

		<p style="padding: 0; font-size: 10px; line-height: 14px; font-family: Verdana; color: #777777; margin: 8px 0 0 0;" >
			<span v-if="formData.logo == 'plts'">
				2000 Center Street, Suite 200 Berkeley, CA 94704
			</span>

			<span v-else>
				60 West Olsen Road <span v-if="formData.mail_code">#{{ formData.mail_code }}</span>&nbsp;|&nbsp; Thousand Oaks, CA 91360
			</span>

			<br v-if="formData.phone || formData.fax" />
			<span v-if="formData.phone">Phone: (805) 493-{{ formData.phone ? formData.phone : "XXXX" }}</span>
			<span v-if="formData.fax">&nbsp;|&nbsp; Fax: (805) 493-{{ formData.fax ? formData.fax : "XXXX" }}</span>
			<br />

			<a :href="'https://www.callutheran.edu/' + formData.website" v-if="formData.logo !=='plts'">CalLutheran.edu{{ formData.website ? '/'+formData.website : '' }}</a>
			<a :href="'https://www.plts.edu/' + formData.website" v-if="formData.logo == 'plts'">PLTS.edu{{ formData.website ? '/'+formData.website : '' }}</a>
		</p>

		<p v-if="formData.social_media_display" style="margin-top: 1em">
			<a :href="formData.social_media.facebook">
				<img src="https://www.callutheran.edu/offices/marketing/brand/email/images/facebook.png" width="24" height="24" />
			</a>
			<a :href="formData.social_media.instagram">
				<img src="https://www.callutheran.edu/offices/marketing/brand/email/images/instagram.png" width="24" height="24" />
			</a>
			<a :href="formData.social_media.twitter">
				<img src="https://www.callutheran.edu/offices/marketing/brand/email/images/twitter.png" width="24" height="24" />
			</a>
			<a :href="formData.social_media.youtube">
				<img src="https://www.callutheran.edu/offices/marketing/brand/email/images/youtube.png" width="24" height="24" />
			</a>
		</p>
	</div>
</template>

<script>
	import Vue from "vue";

	export default {
		name: "Sig",
		props: ["formData"],
		data() {
			return {
				logo_w: "",
				logo_h: ""
			};
		},
		watch: {
			"formData.logo": function(data) {
				var $this = this;
				var img = new Image();
				img.src = this.formData.logos[this.formData.logo];
				img.onload = function() {
					console.log(this.width, this.height);
					$this.logo_w = this.width;
					$this.logo_h = this.height;
				};
			}
		}
	};
</script>