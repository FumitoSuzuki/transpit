<template>
  <div class="text-right">
    <ShareNetwork network="facebook" v-bind="setup">
      <font-awesome-icon icon="fa-brands fa-facebook" style="color:#1877F2" />
    </ShareNetwork>
    <ShareNetwork network="twitter" v-bind="setup" :twitter-user="twitterUser">
      <font-awesome-icon icon="fa-brands fa-twitter" style="color:#1B9DF0" />
    </ShareNetwork>
    <ShareNetwork network="line" v-bind="setup">
      <font-awesome-icon icon="fa-brands fa-line" style="color:#06C755" />
    </ShareNetwork>
    <ShareNetwork network="pinterest" v-bind="setup" :media="media">
      <font-awesome-icon icon="fa-brands fa-pinterest" style="color:#E60023" />
    </ShareNetwork>
  </div>
</template>

<script>
export default {
  props: {
    ogTitle: { type: String, default: 'BBQ TRANSPIT'},
    ogDescript: { type: String, default: 'こだわりのBBQを自宅へお届けいたします' },
    ogUrl: { type: String, default: 'https://bbqtranspit.com/' },
    ogImage: { type: String, default: 'https://bbqtranspit.com/OGP.png' },
    ogType: { type: String, default: 'article' },
    ogSite: { type: String, default: 'BBQ TRANSPIT' },
    twitterCard: { type: String, default: 'summary_large_image' },
    twitterSite: { type: String, default: '' },
    twitterUser: { type: String, default: '' },
    fdAppId: { type: String, default: '' },
    hashTags: { type: String, default: 'vanlife,DIY' },
    media: { type: String, default: 'https://bbqtranspit.com/OGP.png' },
  },
  computed: {
    setup() {
      return {
        url: this.ogUrl,
        title: this.ogTitle,
        description: this.ogDescript,
        quote: this.ogDescript,
        hashtags: this.hashTags,
        twitterUser: this.twitterUser,
      }
    }
  },
}
</script>