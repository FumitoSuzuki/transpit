<template>
  <b-container fluid>
    <b-row>
      <b-col :order="colOrder" :cols="colWidth">
        <b-img fluid :src="`/${slug}/${name}`" :alt="alt" />
      </b-col>
      <b-col order="2">
        <slot />
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
export default {
  props: ['slug', 'name', 'alt', 'width', 'height', 'layout'],
  computed: {
    colOrder() {
      let order = 1
      switch(this.layout) {
        case 'left':
          order = 3
          break
      }
      return order
    },
    colWidth() {
      let width = 6
      switch(this.layout) {
        case 'top':
          width = 12
          break
      }
      return width
    }
  },
  mounted() {}
}
</script>

<style scoped>
.row {
  margin-left: -25px;
  margin-right: -25px;
}
</style>