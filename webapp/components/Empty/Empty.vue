<template>
  <ds-space class="hc-empty" centered :margin="margin">
    <ds-text>
      <img
        :src="iconPath"
        width="80"
        class="hc-empty-icon"
        style="margin-bottom: 5px"
        alt="Empty"
      />
      <br />
      <ds-text v-show="message" class="hc-empty-message" color="softer">
        {{ message }}
      </ds-text>
    </ds-text>
  </ds-space>
</template>

<script>
export default {
  name: 'HcEmpty',
  props: {
    /**
     * Icon that should be shown
     * @options messages|events|alert|tasks|docs|file
     */
    icon: {
      type: String,
      default: 'alert',
      validator: value => {
        return value.match(/(messages|events|alert|tasks|docs|file)/)
      },
    },
    /**
     * Message that appears under the icon
     */
    message: {
      type: String,
      default: null,
    },
    /**
     * Vertical spacing
     */
    margin: {
      type: [String, Object],
      default: 'x-large',
    },
  },
  computed: {
    iconPath() {
      return `/img/empty/${this.icon}.svg`
    },
  },
}
</script>

<style lang="scss">
.hc-empty-icon {
  padding-bottom: $font-space-large;
}
</style>
