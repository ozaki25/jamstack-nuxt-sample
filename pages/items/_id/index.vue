<template>
  <b-container class="bv-example-row">
    <b-card :header="item.title">
      <span v-html="item.body"></span>
    </b-card>
  </b-container>
</template>

<script>
import axios from 'axios'

export default {
  async asyncData({ params, payload }) {
    if (payload) return { item: payload }

    const { data } = await axios.get(
      `https://qiita.com/api/v2/items/${params.id}`,
      {
        headers: { Authorization: `Bearer ${process.env.QIITA_ACCESS_TOKEN}` }
      }
    )
    const item = { id: data.id, title: data.title, body: data.rendered_body }
    return { item }
  }
}
</script>

<style></style>
