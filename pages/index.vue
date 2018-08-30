<template>
  <v-layout row>
    <v-flex xs12 sm6 offset-sm3>
      <v-list two-line>
        <template v-for="(item, index) in items">
          <v-list-tile :key="item.title" avatar ripple>
            <v-list-tile-content>
              <v-list-tile-title>{{ item.name }}</v-list-tile-title>
              <v-list-tile-sub-title class="text--primary">{{ item.title }}</v-list-tile-sub-title>
              <v-list-tile-sub-title>{{ item.group }}</v-list-tile-sub-title>
            </v-list-tile-content>
          </v-list-tile>
          <v-divider v-if="index + 1 < items.length" :key="index"></v-divider>
        </template>
      </v-list>
    </v-flex>
  </v-layout>
</template>

<script>
export default {
  middleware: ['auth'],
  data () {
    return {
      items: []
    }
  },
  methods: {
    async fetchCollection () {
      this.items = await this.$axios.$get('/characters')
    }
  },
  mounted () {
    this.fetchCollection()
  }
}
</script>