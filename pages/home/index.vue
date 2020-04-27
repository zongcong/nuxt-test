<template>
  <div class="center">
    <ul>
      <li v-for="item in obj" :key="item.id" style="padding: 10px 20px">
        <p>{{ item.title }}</p>
        <p class="center" v-html="item.content_rendered"/>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  async asyncData ({ $axios }) {
    const obj = await $axios.$get('/api/topics/hot.json')
    return { obj }
  },
  // data () {
  //   return {
  //     obj: [{ title: '11' }]
  //   }
  // },
  head () {
    return {
      title: `Page 1 (${this.obj[0].title}-side)`,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'Page 1 description'
        }
      ]
    }
  }
}
</script>

<style>
  .center img {
    width: 100%;
  }

  .center ul {
    list-style: none;
    padding: 0;
    line-height: 24px;
    text-align: justify;
    text-indent: 2em;
  }

  .center ul li {
    margin: 5px 0;
    border-bottom: 1px solid #CCC;
  }
</style>
