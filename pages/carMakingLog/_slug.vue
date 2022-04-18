<template>
  <article>
    <b-navbar>
      <b-navbar-brand>
        <b-img width="60px" src="/Logo.svg" alt="BBQ" />
      </b-navbar-brand>
      <b-nav-text><h1>Kitchen car making log</h1></b-nav-text>
    </b-navbar>
    <b-container tag="section" class="mt-2">
      <b-row cols="1">
        <b-col>
          <vue-masonry-wall :items="items" :options="{width: 400, padding: 12}">
            <template v-slot:default="{item}">
              <div :id="item.slug">
              <b-img fluid class="thumbnail" :src="item.thumbnail" />
              <p class="m-0">{{ momentTime(item.createdAt) }}</p>
              <h3>{{ item.title }}</h3>
              <nuxt-content :document="item" />
              <SocialShereButton
                :ogTitle="item.title"
                :ogDescript="item.description"
                :hashTags="item.hashtags"
                :media="`https://${getDomain}${item.thumbnail}`"
                />
              </div>
            </template>
          </vue-masonry-wall>
        </b-col>
      </b-row>
    </b-container>
  </article>
</template>

<script>
import moment from "moment"
export default {
  name: 'CarMakingLogPage',
  async asyncData({ $content, params }){
    const items = await $content('carMakingLog')
      .sortBy('createdAt', 'desc')
      .fetch()
    const slug = await params.slug
    return { items, slug }
  },
  computed: {
    getDomain(){
      return document.domain
    }
  },
  methods: {
    momentTime(time) {
      return moment(time).format("YYYY.MM.DD");
    },
    append() {
      for (let i = 0; i < 20; i++) {
          this.items.push({title: `Item ${this.items.length}`, content: 'Content'})
        }
    },
    scroll() {
      if (this.slug) {
        this.$scrollTo(`#${this.slug}`)
      }
    }
  },
  mounted() {
    setTimeout(this.scroll, 1000)
    console.log(document.domain)
  },
}
</script>

<style scoped>
.col {
  margin-top: 2rem;
  padding-bottom: 2rem;
  border-bottom: 1px solid #666;
}
.col:last-child {
  border-bottom: none;
}
.thumbnail {
  margin-bottom: 1rem;
}
</style>