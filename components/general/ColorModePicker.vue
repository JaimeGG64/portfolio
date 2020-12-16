<template>
  <div class="fixed bottom-0 right-0 m-3">
    <button @click="goToTop()">Back to Top</button>
  </div>
</template>

<script>
import { COLOR_MODE_FALLBACK } from '~/utils/globals.js'
import IconSystem from '~/components/icons/system.svg?inline'
import IconLight from '~/components/icons/light.svg?inline'
import IconDark from '~/components/icons/dark.svg?inline'

export default {
  name: 'ColorModePicker',
  components: {
    IconSystem,
    IconLight,
    IconDark,
  },
  data() {
    return {
      color: COLOR_MODE_FALLBACK,
    }
  },
  watch: {
    '$colorMode.value': {
      immediate: true,
      handler(val) {
        if (!this.$colorMode.unknown) {
          this.color =
            this.$colorMode && this.$colorMode.preference != null && this.$colorMode.preference !== 'null'
              ? this.$colorMode.preference
              : COLOR_MODE_FALLBACK
        } else {
          this.color = COLOR_MODE_FALLBACK
        }
      },
    },
  },
  methods: {
    goToTop() {
      window.scroll({
        top: 100,
        behavior: 'smooth',
      })
    },
  },
}
</script>

<style lang="postcss" scoped>
</style>
