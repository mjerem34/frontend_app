<template>
  <v-content>
    <v-container fluid>
      <v-list>
        <v-list-tile v-for="shop in shops.data" :key="shop.id" :name="shop.attributes.name">
          <v-row align="center" justify="center">
            <v-col cols="10">
              <v-card v-if="shop.attributes.open" color="green lighten-4">
                <v-card-text>
                  <v-row>
                    <v-col cols="12" md="6">
                      <span>{{shop.attributes.name}}</span>
                    </v-col>
                    <v-col cols="12" md="6">
                      <span>Horaires</span>
                      <v-list>
                        <v-list-tile v-for="opening_hour in shop.relationships.opening_hours" :key="opening_hour.day">
                          <strong v-if="opening_hour.is_today">{{opening_hour.formatted_hour}}</strong>
                          <span v-else>{{opening_hour.formatted_hour}}</span>
                          <br>
                        </v-list-tile>
                      </v-list>
                    </v-col>
                  </v-row>
                </v-card-text>
                <v-card-actions>
                  <div class="flex-grow-1"></div>
                  <nuxt-link v-bind:to="'/shops/' + shop.id" >Details</nuxt-link>
                </v-card-actions>
              </v-card>

              <v-card v-else color="red lighten-4">
                <v-card-text>
                  <v-row>
                    <v-col cols="12" md="6">
                      <span>{{shop.attributes.name}}</span>
                    </v-col>
                    <v-col cols="12" md="6">
                      <span>Horaires</span>
                      <v-list>
                        <v-list-tile v-for="opening_hour in shop.relationships.opening_hours" :key="opening_hour.day">
                          <strong v-if="opening_hour.is_today">{{opening_hour.formatted_hour}}</strong>
                          <span v-else>{{opening_hour.formatted_hour}}</span>
                          <br>
                        </v-list-tile>
                      </v-list>
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
