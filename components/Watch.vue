<template>
  <div>
    <!-- <input
      class="w-full text-white pl-[12px] py-[15px] bg-gray-700"
      type="text"
      placeholder="Search..."
    /> -->
    <el-input class="lamp border-red-900" :placeholder="search" v-model="search"></el-input>
    <el-collapse v-model="activeNames" v-if="faqListFiltered.length">
      <el-collapse-item
        :name="index + 1"
        v-for="(item, index) in faqListFiltered"
        :key="index"
      >
        <template slot="title">
          <highlight-code class="text" lang="xlm" :queries="search">
            {{ item.title }}
          </highlight-code>
        </template>
        <div>
          {{ item.content }}
        </div>
      </el-collapse-item>
    </el-collapse>
  </div>
</template>

<script>
import hljs from 'highlight.js'
export default {
  data() {
    return {
      activeNames: ['2'],
      count: 10,
      loading: false,
      search: '',
      faqListFiltered: [],
      activeNames: ['1'],
      faqList: [
        {
          title: 'Does Dinay cider taste the same all over the world? ',
          content:
            'Consistent with real life: in line with the process and logic of real life, and comply with languages and habits that the users are used to; Consistent within interface: all elements should be consistent, such as: design style, icons and texts, position of elements, etc.',
        },
        {
          title: 'Where can I buy Dinay?',
          content:
            'A great question, with a great answer: ingredients and taste can differ slightly across countries. Why’s that, you ask? This can be due to locally sourced ingredients and local food legislation, which make the production slightly different. But now you can get a glass of ice cold Somersby in 50 countries across the globe, and we like to cater to our worldwide fans. That’s why we may also use different ingredients and production methods to satisfy local taste preferences. So make sure you try a Somersby on your travels!',
        },
        {
          title:
            'I have taken a great picture of your cider! Are you interested in using it for marketing purposes?',
          content:
            'A great question, with a great answer: ingredients and taste can differ slightly across countries. Why’s that, you ask? This can be due to locally sourced ingredients and local food legislation, which make the production slightly different. But now you can get a glass of ice cold Somersby in 50 countries across the globe, and we like to cater to our worldwide fans. That’s why we may also use different ingredients and production methods to satisfy local taste preferences. So make sure you try a Somersby on your travels!',
        },
        {
          title: 'Is Dinay a carbonated beverage?',
          content:
            'A great question, with a great answer: ingredients and taste can differ slightly across countries. Why’s that, you ask? This can be due to locally sourced ingredients and local food legislation, which make the production slightly different. But now you can get a glass of ice cold Somersby in 50 countries across the globe, and we like to cater to our worldwide fans. That’s why we may also use different ingredients and production methods to satisfy local taste preferences. So make sure you try a Somersby on your travels!',
        },
      ],
    }
  },
  watch: {
    search(newValue, oldValue) {
      this.filterFaq(newValue)
    },
  },
  computed: {
  },
  methods: {
    handleChange(val) {
      console.log(val)
    },
    filterFaq(newValue) {
      this.faqListFiltered = this.faqList.filter((item) => {
        return item.title.toLowerCase().includes(newValue.toLowerCase())
      })
    },
  },
  mounted() {
    this.filterFaq(this.search)
  },
}
</script>

<style scoped>
.red {
  color: red;
}
</style>
