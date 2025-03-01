<template>
  <div>
    <h1 class="mb-8 font-bold text-3xl">
      <inertia-link
        class="text-indigo-500 hover:text-indigo-800"
        :href="$routes.admin_contacts()"
      >
        Contacts
      </inertia-link>
      <span class="text-indigo-400 font-medium">/</span>
      {{ form.first_name }} {{ form.last_name }}
    </h1>
    <trashed-message
      v-if="contact.deleted_at"
      class="mb-6"
      @restore="restore"
    >
      This contact has been deleted.
    </trashed-message>
    <div class="bg-white rounded shadow overflow-hidden max-w-3xl">
      <contact-form
        :form="form"
        :organizations="organizations"
        @submit="submit"
      >
        <div class="px-8 py-4 bg-gray-100 border-t border-gray-200 flex items-center">
          <button
            v-if="!contact.deleted_at"
            class="text-red-700 hover:underline"
            tabindex="-1"
            type="button"
            @click="destroy"
          >
            Delete Contact
          </button>
          <loading-button
            :loading="sending"
            class="btn-indigo ml-auto"
            type="submit"
          >
            Update Contact
          </loading-button>
        </div>
      </contact-form>
    </div>
  </div>
</template>

<script>
// import Layout from '~/components/Layouts/Main'
import LoadingButton from '~/components/LoadingButton'
import ContactForm from './Form'
import TrashedMessage from '~/components/TrashedMessage'
import _ from 'lodash'

export default {
  metaInfo() {
    return {
      title: `${this.form.first_name} ${this.form.last_name}`,
    }
  },
  layout: 'dashboard',
  components: {
    LoadingButton,
    ContactForm,
    TrashedMessage,
  },
  props: {
    contact: {
      type: Object,
      required: true,
    },
    organizations: {
      type: Array,
      required: true,
    },
  },
  remember: 'form',
  data() {
    return {
      sending: false,
      form: _.omit(this.contact, 'id', 'deleted_at'),
    }
  },
  methods: {
    submit() {
      this.sending = true
      this.$inertia
        .put(this.$routes.admin_contact(this.contact.id), this.form)
        .then(() => (this.sending = false))
    },
    destroy() {
      if (confirm('Are you sure you want to delete this contact?')) {
        this.$inertia.delete(this.$routes.admin_contact(this.contact.id))
      }
    },
    restore() {
      if (confirm('Are you sure you want to restore this contact?')) {
        this.$inertia.put(this.$routes.admin_restore_contact(this.contact.id))
      }
    },
  },
}
</script>
