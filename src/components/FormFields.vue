<template>
  <form class="form-fields">
    <div class="form-item">
      <label for="name">Name</label>
      <input v-model="formData.name" type="text" required />
    </div>

    <div class="form-item">
      <label for="pronouns">Pronouns</label>
      <select id="pronouns" v-model="formData.pronouns">
		  <option></option>
        <option value="he/him/his">He/Him/His</option>
        <option value="she/her/hers">She/Her/Hers</option>
        <option value="they/them/theirs">They/Them/Theirs</option>
        <option value="custom">Custom</option>
      </select>
      <input v-model="formData.pronouns_custom" type="text" v-if="formData.pronouns == 'custom'" />
    </div>

    <div class="form-item">
      <label for="title">Title</label>
      <input v-model="formData.title" type="text" required />
    </div>

    <div class="form-item">
      <label for="department">Department</label>
      <input v-model="formData.department" type="text" />
    </div>

    <div class="form-item">
      <label for="mail_code">Mail Code</label>
      <input v-model="formData.mail_code" type="text" />
    </div>

    <div class="form-item">
      <label for="phone">Phone</label>
      <input v-model="formData.phone" type="text" />
    </div>

    <div class="form-item">
      <label for="fax">Fax</label>
      <input v-model="formData.fax" type="text" />
    </div>
  </form>
</template>

<script>
import Vue from "vue";

export default {
	name: 'FormFields',
	props: ['formData']
};
</script>

<style>
</style>