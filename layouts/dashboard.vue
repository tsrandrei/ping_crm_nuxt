<template>
  <core-portal>
    <div class="flex flex-col">
      <div class="h-screen flex flex-col" @click="hideDropdownMenus">
        <core-topbar />
        <div class="flex flex-grow overflow-hidden">
          <core-main-menu />
          <nuxt class="flex-1 px-4 py-8 md:p-12 overflow-x-auto" scroll-region />
        </div>
      </div>
    </div>
    <core-view />
  </core-portal>
</template>

<script>
  // import coreFilter from '~/components/core/AppFilter';
  // import coreToolbar from '~/components/core/AppToolbar';
  import coreTopbar from '~/components/core/app-topbar';
  import coreMainMenu from '~/components/core/app-main-menu';
  import corePortal from '~/components/core/app-portal';
  // import coreView from '~/components/core/AppView';

  export default {
    head: {
      htmlAttrs: {
        class: 'h-full bg-gray-200'
      },
      bodyAttrs: {
        class: 'font-sans leading-none text-gray-800 antialiased'
      }
    },
    components: {
      // coreFilter,
      // coreToolbar,
      corePortal,
      coreTopbar,
      coreMainMenu,
      // coreView
    }
  }
</script>
