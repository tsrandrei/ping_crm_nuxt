<template>
  <div>
    <h1 class="mb-8 font-bold text-3xl">
      <inertia-link
        class="text-indigo-500 hover:text-indigo-800"
        :href="$routes.admin_organizations()"
      >
        Organizations
      </inertia-link>
      <span class="text-indigo-400 font-medium">/</span>
      {{ form.name }}
    </h1>
    <trashed-message
      v-if="organization.deleted_at"
      class="mb-6"
      @restore="restore"
    >
      This organization has been deleted.
    </trashed-message>
    <div class="bg-white rounded shadow overflow-hidden max-w-3xl">
      <organization-form
        :form="form"
        @submit="submit"
      >
        <div class="px-8 py-4 bg-gray-100 border-t border-gray-200 flex items-center">
          <button
            v-if="!organization.deleted_at"
            class="text-red-700 hover:underline"
            tabindex="-1"
            type="button"
            @click="destroy"
          >
            Delete Organization
          </button>
          <loading-button
            :loading="sending"
            class="btn-indigo ml-auto"
            type="submit"
          >
            Update Organization
          </loading-button>
        </div>
      </organization-form>
    </div>
    <h2 class="mt-12 font-bold text-2xl">
      Contacts
    </h2>
    <div class="mt-6 bg-white rounded shadow overflow-x-auto">
      <table class="w-full whitespace-no-wrap">
        <tr class="text-left font-bold">
          <th class="px-6 pt-6 pb-4">
            Name
          </th>
          <th class="px-6 pt-6 pb-4">
            City
          </th>
          <th
            class="px-6 pt-6 pb-4"
            colspan="2"
          >
            Phone
          </th>
        </tr>
        <tr
          v-for="contact in contacts"
          :key="contact.id"
          class="hover:bg-gray-100 focus-within:bg-gray-100"
        >
          <td class="border-t">
            <inertia-link
              class="px-6 py-4 flex items-center focus:text-indigo-500"
              :href="$routes.edit_admin_contact(contact.id)"
            >
              {{ contact.name }}
              <icon
                v-if="contact.deleted_at"
                name="trash"
                class="flex-shrink-0 w-3 h-3 fill-gray-500 ml-2"
              />
            </inertia-link>
          </td>
          <td class="border-t">
            <inertia-link
              class="px-6 py-4 flex items-center"
              :href="$routes.edit_admin_contact(contact.id)"
              tabindex="-1"
            >
              {{ contact.city }}
            </inertia-link>
          </td>
          <td class="border-t">
            <inertia-link
              class="px-6 py-4 flex items-center"
              :href="$routes.edit_admin_contact(contact.id)"
              tabindex="-1"
            >
              {{ contact.phone }}
            </inertia-link>
          </td>
          <td class="border-t w-px">
            <inertia-link
              class="px-4 flex items-center"
              :href="$routes.edit_admin_contact(contact.id)"
              tabindex="-1"
            >
              <icon
                name="cheveron-right"
                class="block w-6 h-6 fill-gray-500"
              />
            </inertia-link>
          </td>
        </tr>
        <tr v-if="contacts.length === 0">
          <td
            class="border-t px-6 py-4"
            colspan="4"
          >
            No contacts found.
          </td>
        </tr>
      </table>
    </div>
  </div>
</template>

<script>
import Icon from '~/components/Icon'
import LoadingButton from '~/components/LoadingButton'
import OrganizationForm from './Form'
import TrashedMessage from '~/components/TrashedMessage'
import _ from 'lodash'

export default {
  metaInfo() {
    return { title: this.form.name }
  },
  layout: 'dashboard',
  components: {
    Icon,
    LoadingButton,
    OrganizationForm,
    TrashedMessage,
  },
  props: {
    organization: {
      type: Object,
      required: true,
    },
    contacts: {
      type: Array,
      required: true,
    },
  },
  remember: 'form',
  data() {
    return {
      sending: false,
      form: _.omit(this.organization, 'id', 'deleted_at'),
    }
  },
  methods: {
    submit() {
      this.sending = true
      this.$inertia
        .put(this.$routes.admin_organization(this.organization.id), this.form)
        .then(() => (this.sending = false))
    },
    destroy() {
      if (confirm('Are you sure you want to delete this organization?')) {
        this.$inertia.delete(this.$routes.admin_organization(this.organization.id))
      }
    },
    restore() {
      if (confirm('Are you sure you want to restore this organization?')) {
        this.$inertia.put(
          this.$routes.restore_organization(this.organization.id),
        )
      }
    },
  },
}
</script>
