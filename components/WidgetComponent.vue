<template>
  <div v-if="info" class="widget__wrapper">
    <div class="widget">
      <span>{{ info.cows }}</span> <br />коров
    </div>
    <div class="widget">
      <span>{{ info.rabbits }}</span> <br />
      кроликов
    </div>
    <div class="widget">
      <span>{{ info.sheeps }}</span> <br />
      овечек
    </div>
  </div>
</template>
<script>
import { mapGetters } from 'vuex'
export default {
  name: 'WidgetComponent',
  data() {
    return {
      info: null,
    }
  },
  computed: {
    ...mapGetters({
      infoData: 'mainpage/getWidget',
    }),
  },
  async mounted() {
    const data = await this.infoData
    this.info = data.data
  },
}
</script>

<style>
.widget {
  padding: 20px;
  border-radius: 10px;
  background: #cce6ea94;
  -webkit-box-shadow: 4px 4px 0px 0px rgb(34 60 80 / 20%);
  -moz-box-shadow: 4px 4px 0px 0px rgb(34 60 80 / 20%);
  box-shadow: 4px 4px 0px 0px rgb(34 60 80 / 20%);
}
.widget__wrapper {
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  align-items: stretch;
  margin: 20px 20px;
}
.widget span {
  font-size: 42px;
}
</style>
