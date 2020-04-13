<template>
  <div class="md:flex flex-shrink-0">
    <div class="bg-indigo-900 md:flex-shrink-0 md:w-56 px-6 py-4 flex items-center justify-between md:justify-center">
      <a class="mt-1" aria-label="Home" role="navigation">
        <logo class="fill-white" width="120" height="28"/>
      </a>
      <dropdown class="md:hidden" placement="bottom-end" aria-label="Main menu">
        <svg class="fill-white w-6 h-6" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"><path d="M0 3h20v2H0V3zm0 6h20v2H0V9zm0 6h20v2H0v-2z" /></svg>
        <div slot="dropdown" class="mt-2 px-8 py-4 shadow-lg bg-indigo-800 rounded">
        </div>
      </dropdown>
    </div>

    <div class="bg-white border-b w-full p-4 md:py-0 md:px-12 text-sm md:text-md flex justify-between items-center">
      <div class="mt-1 mr-4">
         Acme Corporation
      </div>
      <dropdown class="mt-1" placement="bottom-end" aria-label="User menu"  v-on:click="showhide">
        <div class="flex items-center cursor-pointer select-none group">
          <div class="text-gray-800 group-hover:text-indigo-600 focus:text-indigo-600 mr-1 whitespace-no-wrap">
            <span>John</span>
            <span class="hidden md:inline">Doe</span>
          </div>
          <icon class="w-5 h-5 group-hover:fill-indigo-600 fill-gray-800 focus:fill-indigo-600" name="cheveron-down"/>
        </div>

        <div v-show="collapsed" slot="dropdown" class="mt-2 py-2 shadow-xl bg-white rounded text-sm">
          <nuxt-link to="/" class="block px-6 py-2 hover:bg-indigo-600 hover:text-white" role="navigation">
            My Profile
          </nuxt-link>
          <nuxt-link to="/" class="block px-6 py-2 hover:bg-indigo-600 hover:text-white" role="navigation">
            Manage Users
          </nuxt-link>
          <nuxt-link to="/" class="block px-6 py-2 hover:bg-indigo-600 hover:text-white" method="delete">
            Logout
          </nuxt-link>
        </div>
      </dropdown>

    </div>
  </div>
</template>

<script>
// import Dropdown from '~/components/Dropdown'
import Icon from '~/components/Icon'
import Logo from '~/components/Logo'
import MainMenu from '~/components/core/app-main-menu'

export default {
  components: {
    MainMenu,
    // Dropdown,
    Icon,
    Logo,
  },
  data() {
    return {
      showUserMenu: false,
      accounts: null,
    }
  },
  methods: {
    url() {
      return '/'
    },
    hideDropdownMenus() {
      this.showUserMenu = false
    },
    showhide: function() {
    if (!this.collapsed)
        this.collapsed = true;
    else
        this.collapsed = false;
    },
  },
}
</script>
