<template>
  <div
    class="fixed z-50 top-0 left-0 w-full h-full bg-white lg:hidden"
    :hidden="!$store.state.ui.isBurgerMenuOpen"
  >
    <div class="bg-primary-light bg-opacity-60 h-full">
      <div class="container flex flex-col justify-between h-full py-block-0.5 overflow-auto">
        <div>
          <LogoOm
            class="w-44 h-auto"
          />

          <button
            class="w-10 sm:w-14 h-10 sm:h-14 bg-primary text-white flex items-center justify-center absolute top-block-0.75 right-block-0.5"
            @click="() => $store.commit('ui/setIsBurgerMenuOpen', false)"
          >
            <svg xmlns="http://www.w3.org/2000/svg" width="11.314" height="11.314" viewBox="0 0 11.314 11.314">
              <g transform="translate(-327.344 -51.343)" fill="currentColor">
                <path transform="rotate(45 102.403 422.518)" d="M0 0h14v2H0z" />
                <path transform="rotate(135 158.402 96.517)" d="M0 0h14v2H0z" />
              </g>
            </svg>
          </button>
        </div>

        <nav class="flex flex-col gap-block-0.5 py-block-1">
          <nuxt-link
            v-for="(item, index) in menuItems"
            :key="index"
            :to="localePath(item.link)"
            class="NavItem uppercase text-base text-primary font-semibold hover:underline"
            v-text="item.text"
          />

          <!-- <nuxt-link
            :to="switchLocalePath($i18n.locale === 'cs' ? 'en' : 'cs')"
            class="uppercase text-sm font-semibold ml-10 text-secondary"
          >
            {{ $i18n.locale === 'cs' ? 'en' : 'cz' }}
          </nuxt-link> -->
        </nav>

        <Socials />
      </div>
    </div>
  </div>
</template>

<script>
import LogoOm from '~/assets/img/logo-om.svg?inline';

export default {
  components: {
    LogoOm,
  },
  computed: {
    menuItems() {
      return this.$store.state.content.global.menuItems;
    },
  },
};
</script>

<style lang="scss" scoped>
.NavItem.is-active {
  @apply text-secondary;
}
</style>
