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
export default {
  data() {
    return {
      items: [
        { id: 1, title: 'test' },
        { id: 2, title: 'test' },
        { id: 3, title: 'test' }
      ]
    }
  }
}
</script>

<style></style>
