<template>
  <b-container class="bv-example-row">
    <b-card header="新着記事一覧">
      <ul>
        <li v-for="item in items" :key="item.id">
          {{ item.title }}
        </li>
      </ul>
    </b-card>
  </b-container>
</template>

<script>
import axios from 'axios'

export default {
  async asyncData() {
    const { data } = await axios.get('https://qiita.com/api/v2/items')
    const items = data.map(({ id, title, url }) => ({ id, title, url }))
    return { items }
  }
}
</script>

<style></style>
