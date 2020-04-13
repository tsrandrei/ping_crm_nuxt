<template>
  <div>
    <div class="mb-4">
      <inertia-link
        class="flex items-center group py-3" role="navigation" aria-label="Dashboard">
        <icon
          name="dashboard"
          class="w-4 h-4 mr-2"
          :class="isUrl('') ? 'fill-white' : 'fill-indigo-400 group-hover:fill-white'"
        />
        <div :class="isUrl('') ? 'text-white' : 'text-indigo-300 group-hover:text-white'">
          Dashboard
        </div>
      </inertia-link>
    </div>
    <div class="mb-4">
      <inertia-link
        class="flex items-center group py-3"
        role="navigation"
        aria-label="Organizations"
      >
        <icon
          name="office"
          class="w-4 h-4 mr-2"
          :class="isUrl('organizations') ? 'fill-white' : 'fill-indigo-400 group-hover:fill-white'"
        />
        <div :class="isUrl('organizations') ? 'text-white' : 'text-indigo-300 group-hover:text-white'">
          Organizations
        </div>
      </inertia-link>
    </div>
    <div class="mb-4">
      <inertia-link
        class="flex items-center group py-3"
        role="navigation"
        aria-label="Contacts"
      >
        <icon
          name="users"
          class="w-4 h-4 mr-2"
          :class="isUrl('contacts') ? 'fill-white' : 'fill-indigo-400 group-hover:fill-white'"
        />
        <div :class="isUrl('contacts') ? 'text-white' : 'text-indigo-300 group-hover:text-white'">
          Contacts
        </div>
      </inertia-link>
    </div>
    <div class="mb-4">
      <inertia-link
        class="flex items-center group py-3"
        role="navigation"
        aria-label="Reports"
      >
        <icon
          name="printer"
          class="w-4 h-4 mr-2"
          :class="isUrl('reports') ? 'fill-white' : 'fill-indigo-400 group-hover:fill-white'"
        />
        <div :class="isUrl('reports') ? 'text-white' : 'text-indigo-300 group-hover:text-white'">
          Reports
        </div>
      </inertia-link>
    </div>
    <div class="mb-4">
      <inertia-link
              class="flex items-center group py-3"
              role="navigation"
              aria-label="Reports"
      >
        <Settings24 class="mr-2" :class="isUrl('reports') ? 'fill-white' : 'fill-indigo-400 group-hover:fill-white'" />
        <div :class="isUrl('reports') ? 'text-white' : 'text-indigo-300 group-hover:text-white'">
          Settings
        </div>
      </inertia-link>
    </div>
    <div class="mb-4">
      <inertia-link
              class="flex items-center group py-3"
              role="navigation"
              aria-label="Reports"
      >
        <Settings24 class="mr-2" :class="isUrl('reports') ? 'fill-white' : 'fill-indigo-400 group-hover:fill-white'" />
        <div :class="isUrl('reports') ? 'text-white' : 'text-indigo-300 group-hover:text-white'">
          Snap
        </div>
      </inertia-link>
    </div>
    <div class="mb-4">
      <inertia-link
              class="flex items-center group py-3"
              role="navigation"
              aria-label="Reports"
      >
        <Settings24 class="mr-2" :class="isUrl('reports') ? 'fill-white' : 'fill-indigo-400 group-hover:fill-white'" />
        <div :class="isUrl('reports') ? 'text-white' : 'text-indigo-300 group-hover:text-white'">
          Lists
        </div>
      </inertia-link>
    </div>
  </div>
</template>

<script>
import Icon from '~/components/Icon.vue'
// import CarbonIconsVue  from '@carbon/icons-vue'
// import Settings24 from '@carbon/icons-vue/es/settings/24'


export default {

  components: {
    Icon,
    // Settings24
  },
  props: {
    url: {
      type: String,
      required: true,
    },
  },
  methods: {
    isUrl(...urls) {
      if (urls[0] === '') {
        return this.url === ''
      }

      // return urls.filter(url => this.url.startsWith(url)).length
    },
  },
}
</script>
