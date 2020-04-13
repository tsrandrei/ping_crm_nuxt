<template>
  <div>
    <div>
    <h1 class="mb-8 font-bold text-3xl">
      Dashboard
    </h1>
    <p class="mb-12 leading-normal">
      Hey there! Welcome to Ping CRM, a demo app designed to help illustrate how
      <a
        class="text-indigo-800 underline hover:text-orange-600 font-bold"
        href="https://inertiajs.com"
      >
        Inertia.js
      </a> works with
      <a
        href="https://rubyonrails.org/"
        class="text-indigo-800 underline hover:text-orange-600 font-bold"
      >
        Ruby on Rails
      </a>.
    </p>

    <p class="mb-10 leading-normal">
      Version
      <a class="hover:underline">

      </a>
      &minus;
      {{ relativeCommitTime }}
    </p>

    <div>
      <button
        class="btn-indigo"

      >
        500 error
      </button>
      <button
        class="ml-2 btn-indigo"
        href="/error-404"
      >
        404 error
      </button>
    </div>
  </div>
  </div>
</template>

<script>
// import MinimalLayout from '@/Layouts/Minimal'
// import Dropdown from '@/Shared/Dropdown'
// import Icon from '@/Shared/Icon'
// import Logo from '@/Shared/Logo'
// import MainMenu from '~/components/MainMenu.vue'

// import Logo from '~/components/pinx.vue'

export default {
  layout: 'dashboard',
  components: {
    // Logo
  },
  props: {
    git: {
      type: Object,
      required: true,
    },
  },
  computed: {
    relativeCommitTime() {
      return 'this'
    },
  },
}
</script>

<style>
.btn-indigo {
  @apply px-6 py-3 rounded bg-indigo-600 text-white text-sm font-bold whitespace-no-wrap;

  &:hover,
  &:focus {
    @apply bg-orange-500
  }
}

.btn-spinner,
.btn-spinner:after {
  border-radius: 50%;
  width: 1.5em;
  height: 1.5em;
}

.btn-spinner {
  font-size: 10px;
  position: relative;
  text-indent: -9999em;
  border-top: .2em solid white;
  border-right: .2em solid white;
  border-bottom: .2em solid white;
  border-left: .2em solid transparent;
  transform: translateZ(0);
  animation: spinning 1s infinite linear;
}

@keyframes spinning {
  0% {
    transform: rotate(0deg)
  }

  100% {
    transform: rotate(360deg)
  }
}

</style>
