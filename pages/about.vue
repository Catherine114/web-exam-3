<template>
  <div>
    <div v-if="info">
      <h1 class="heading">Страница о нашем роддоме</h1>

      <p class="about__text" v-html="info.text"></p>
    </div>
    <LoaderComponent v-else />
  </div>
</template>
<script>
import { mapGetters } from 'vuex'
import LoaderComponent from '@/components/LoaderComponent.vue'
export default {
  name: 'AboutPage',
  components: { LoaderComponent },
  layout: 'DefaultLayout',
  data() {
    return {
      info: null,
    }
  },
  computed: {
    ...mapGetters({
      infoData: 'mainpage/getAboutPage',
    }),
  },
  async mounted() {
    const data = await this.infoData
    this.info = data.data
  },
}
</script>

<style>
.about__text {
  padding: 20px;
}
</style>
