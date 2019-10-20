<template>
  <component :is="layout"></component>
</template>

<script>
const DefaultLayout = () => import(/* webpackChunkName: "base" */ "@/layouts/base.layout");
export default {
  computed: {
    layout() {
      return this.$route.meta.layout || DefaultLayout;
    }
  }
};
</script>
