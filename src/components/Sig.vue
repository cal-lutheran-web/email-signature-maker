<template>
<div class="sig">
	<p style="padding: 0; font-size: 12px; line-height: 15px; font-family: Verdana; color: #3b2360; margin: 0 0 15px 0;">
			<b>{{ formData.name }}</b><br>
			<span v-if="formData.pronouns"><strong>Pronouns:</strong> {{ formData.pronouns_display }}<br /></span>
			<i>{{ formData.title }}<br>
			<span v-if="formData.department">{{ formData.department }}</span></i>
		</p>
		<img src="https://www.callutheran.edu/offices/marketing/brand/images/CLU-default-signature.png" alt="California Lutheran University" width="250" height="24">
		<p style="padding: 0; font-size: 10px; line-height: 14px; font-family: Verdana; color: #777777; margin: 8px 0 0 0;">
			60 West Olsen Road #{{ formData.mail_code }} &nbsp;|&nbsp; Thousand Oaks, CA 91360<br>
			<span v-if="formData.phone">Phone: (805) 493-{{ formData.phone }} </span><span v-if="formData.fax">&nbsp;|&nbsp; Fax: (805) 493-{{ formData.fax }}</span><br>
			<a href="https://www.callutheran.edu">CalLutheran.edu</a>
	</p>
	</div>
</template>

<script>
export default {
	name: 'Sig',
	props: ['formData']
}
</script>

<style>

</style>