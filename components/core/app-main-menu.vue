<template>
  <div class="bg-indigo-800 flex-shrink-0 w-56 p-12 hidden md:block overflow-y-auto">
    <div class="mb-4">
      <nuxt-link to="/dashboard" class="flex items-center group py-3" role="navigation" aria-label="Dashboard">
        <icon name="dashboard" class="w-4 h-4 mr-2" :class="isUrl('') ? 'fill-white' : 'fill-indigo-400 group-hover:fill-white'"/>
        <div :class="isUrl('') ? 'text-white' : 'text-indigo-300 group-hover:text-white'">
          Dashboard
        </div>
      </nuxt-link>
    </div>
    <div class="mb-4">
      <nuxt-link to="/organisations/index" class="flex items-center group py-3" role="navigation" aria-label="Organizations">
        <icon
          name="office"
          class="w-4 h-4 mr-2"
          :class="isUrl('organizations') ? 'fill-white' : 'fill-indigo-400 group-hover:fill-white'"
        />
        <div :class="isUrl('organizations') ? 'text-white' : 'text-indigo-300 group-hover:text-white'">
          Organizations
        </div>
      </nuxt-link>
    </div>
    <div class="mb-4">
      <nuxt-link
        to="/dashboard"
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
      </nuxt-link>
    </div>
    <div class="mb-4">
      <nuxt-link
        to="/dashboard"
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
      </nuxt-link>
    </div>
    <div class="mb-4">
      <nuxt-link
        to="/dashboard"
        class="flex items-center group py-3"
        role="navigation"
        aria-label="Reports"
      >
        <Settings24 class="mr-2" :class="isUrl('reports') ? 'fill-white' : 'fill-indigo-400 group-hover:fill-white'" />
        <div :class="isUrl('reports') ? 'text-white' : 'text-indigo-300 group-hover:text-white'">
          Settings
        </div>
      </nuxt-link>
    </div>
    <div class="mb-4">
      <nuxt-link
        to="/dashboard"
        class="flex items-center group py-3"
        role="navigation"
        aria-label="Reports"
      >
        <Settings24 class="mr-2" :class="isUrl('reports') ? 'fill-white' : 'fill-indigo-400 group-hover:fill-white'" />
        <div :class="isUrl('reports') ? 'text-white' : 'text-indigo-300 group-hover:text-white'">
          Snap
        </div>
      </nuxt-link>
    </div>
    <div class="mb-4">
      <nuxt-link
        to="/dashboard"
        class="flex items-center group py-3"
        role="navigation"
        aria-label="Reports"
      >
        <Settings24 class="mr-2" :class="isUrl('reports') ? 'fill-white' : 'fill-indigo-400 group-hover:fill-white'" />
        <div :class="isUrl('reports') ? 'text-white' : 'text-indigo-300 group-hover:text-white'">
          Lists
        </div>
      </nuxt-link>
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
