<template>
  <div>
    <h1 class="mb-8 font-bold text-3xl">
      <inertia-link
        class="text-indigo-400 hover:text-indigo-600"
        :href="$routes.admin_contacts()"
      >
        Contacts
      </inertia-link>
      <span class="text-indigo-400 font-medium">/</span> Create
    </h1>
    <div class="bg-white rounded shadow overflow-hidden max-w-3xl">
      <contact-form
        :form="form"
        :organizations="organizations"
        @submit="submit"
      >
        <div class="px-8 py-4 bg-gray-100 border-t border-gray-200 flex justify-end items-center">
          <loading-button
            :loading="sending"
            class="btn-indigo"
            type="submit"
          >
            Create Contact
          </loading-button>
        </div>
      </contact-form>
    </div>
  </div>
</template>

<script>
import LoadingButton from '~/components/LoadingButton'
import ContactForm from './Form'

export default {
  metaInfo: { title: 'Create Contact' },
  layout: 'dashboard',
  components: {
    LoadingButton,
    ContactForm,
  },
  props: {
    organizations: {
      type: Array,
      required: true,
    },
  },
  remember: 'form',
  data() {
    return {
      sending: false,
      form: {},
    }
  },
  methods: {
    submit() {
      this.sending = true
      this.$inertia
        .post(this.$routes.admin_contacts(), this.form)
        .then(() => (this.sending = false))
    },
  },
}
</script>
