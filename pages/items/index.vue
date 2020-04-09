<template>
  <b-container class="bv-example-row">
    <b-card header="新着記事一覧" no-body>
      <b-list-group flush>
        <b-list-group-item
          v-for="item in items"
          :key="item.id"
          :to="`/items/${item.id}`"
        >
          {{ item.title }}
        </b-list-group-item>
      </b-list-group>
    </b-card>
  </b-container>
</template>

<script>
import axios from 'axios'

export default {
  async asyncData() {
    const { data } = await axios.get('https://qiita.com/api/v2/items', {
      headers: { Authorization: `Bearer ${process.env.QIITA_ACCESS_TOKEN}` }
    })
    const items = data.map((item) => ({ id: item.id, title: item.title }))
    return { items }
  }
}
</script>

<style></style>
