<template>
  <v-app class="grey lighten-4">
    <v-container grid-list-md class="my-5">
      <v-card class="pa-3 mb-2" v-for="data in myJson" :key="data.id">
      <v-layout row>
        <v-flex style="max-width: 65px">
      <v-layout column mr-1>
                <v-flex>
            <v-avatar class="black" size="48">
            </v-avatar>
        </v-flex>

        <v-flex>
          <v-layout right column>
            <v-flex>
              <v-icon medium>expand_less</v-icon>
            </v-flex>
            <v-flex>
              <div style="text-align: center">{{data.vote.votes}}</div>
            </v-flex>
            <v-flex>
              <v-icon medium>expand_more</v-icon>
            </v-flex>
          </v-layout>
        </v-flex>
      </v-layout>
      </v-flex>

      <v-flex xs10 sm11>
      <v-layout row style="margin-bottom: 5%">
          <v-flex xs4 sm6>
            <v-layout row wrap align-center>
              <v-flex sm5 order-sm1 order-xs2 >
                <v-chip class="px-1" small dark>
                  <span class="font-italic font-weight-medium">SpitBaller</span>
                </v-chip>
              </v-flex>

              <v-flex sm7 order-sm2 order-xs1>
                <div class="text-align: center">{{convertDate(data.dateTime)}}</div>
              </v-flex>
            </v-layout>
      </v-flex>

        <v-spacer></v-spacer>

        <v-flex xs5>
          <v-layout>
            <v-flex xs10 v-if="data.price > 0">
               <h2 class="right" v-if="data.price > 0">{{convertPrice(data.price)}} Pts</h2>
            </v-flex>
            <v-flex align-end>
              <div class="right">
               <v-icon>more_vert</v-icon>
              </div>
            </v-flex>
          </v-layout>
 
        </v-flex>
      </v-layout>
        <v-layout>
          <v-flex xs12 class="grey lighten-2 pa-3">
          <v-layout>
            <v-layout column>
              <v-flex xs11>
                <h3>{{data.title}}</h3>
              </v-flex>
              <v-flex xs11>
                <div style="overflow-wrap: break-word">{{data.snippet}}</div>
              </v-flex>
            </v-layout>
            <v-flex xs1 style="max-width: 24px">
              <v-icon small>description</v-icon>
            </v-flex>
          </v-layout>
        </v-flex>        
        </v-layout>

        <v-layout>
          <v-flex xs11>
            <div>{{data.university}} * {{data.course}}</div>
          </v-flex>        
        </v-layout>
        
      <v-layout row right>
          <v-flex xs12>
          <v-icon small right class="mr-1">cloud_download</v-icon>
          <span>{{data.downloads}}</span>
          <v-icon small right class="mr-1">remove_red_eye</v-icon>
          <span>{{data.views}}</span>
          </v-flex>
      </v-layout>
      </v-flex>
      </v-layout>
      </v-card>
    </v-container>
  </v-app>
</template>

<script>
  
  import json from './assets/data.json'
  export default {
    name: 'App',
    data(){
      return{
        myJson: json
      }
    },
        methods: {
          convertDate(prop){
            const date = new Date(prop).toString().split(' ')
            const forematedDate = `${date[1]} ${date[2]}, ${date[3]}`
            return forematedDate
          },
          convertPrice(prop){
          const formatPrice = prop.toFixed(2)
          return formatPrice
          }
        }

  }
</script>


<style>
  .theme--light.v-sheet{
    max-width: 640px;
    min-width: 392px;
    margin: auto;

  }
</style>

