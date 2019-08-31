<template>
  <v-content>
    <v-container fluid>
      <v-list>
        <v-list-tile v-for="shop in shops" :key="shop.id" :name="shop.name">
          <v-row align="center" justify="center">
            <v-col cols="10">
              <v-card>
                <v-card-text>
                  <v-row>
                    <v-col cols="12" md="6">
                      <span>{{shop.name}}</span>
                    </v-col>
                    <v-col cols="12" md="6">
                      <span>Horaires</span>
                    </v-col>
                  </v-row>
                </v-card-text>
                <v-card-actions>
                  <div class="flex-grow-1"></div>
                  <nuxt-link v-bind:to="'/shops/' + shop.id" >Details</nuxt-link>
                </v-card-actions>
              </v-card>
            </v-col>
          </v-row>
        </v-list-tile>
      </v-list>
    </v-container>
  </v-content>
</template>

<script>
export default {
  data () {
    return {
      shops: []
    }
  },
  methods: {
    async updateExamples() {
      this.shops = await this.$axios.$get('/shops')
    }
  },
  mounted () {
    this.updateExamples()
  }
}
</script>
