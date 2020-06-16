<template>
  <div class="about">
    <v-subheader>About</v-subheader>
    
    <v-container>
      <v-layout row wrap>
        <v-flex sm4 xs12>
           <v-card class="mr-10 ma-5">
             <v-card-text>
               <div>Word of the Day</div>
                  <p class="display-1 text--primary">
                    be•nev•o•lent
                  </p>
                  <p>adjective</p>
                  <div class="text--primary">
                    well meaning and kindly.<br>
                    "a benevolent smile"
                </div>
             </v-card-text>
            <v-card-actions>
              <v-btn
                text
                color="deep-purple accent-4"
              >
                Learn More
              </v-btn>
            </v-card-actions>
           </v-card>
        </v-flex>

        <v-flex sm4 xs12 >
          <v-card
            class="mr-10 ma-5"
            max-width="400"
          >
            <v-img
              class="white--text align-end"
              height="200px"
              src="https://cdn.vuetifyjs.com/images/cards/docks.jpg"
            >
              <v-card-title>Top 10 Australian beaches</v-card-title>
            </v-img>

            <v-card-subtitle class="pb-0">Number 10</v-card-subtitle>

            <v-card-text class="text--primary">
              <div>Whitehaven Beach</div>

              <div>Whitsunday Island, Whitsunday Islands</div>
            </v-card-text>

            <v-card-actions>
              <v-btn
                color="orange"
                text
              >
                Share
              </v-btn>

              <v-btn
                color="orange"
                text
              >
                Explore
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-flex>

        <v-flex sm4 xs12 >
          <v-card
            class="mr-12 ma-5"
            max-width="344"
          >
            <v-img
              src="https://cdn.vuetifyjs.com/images/cards/sunshine.jpg"
              height="200px"
            ></v-img>

            <v-card-title>
              Top western road trips
            </v-card-title>

            <v-card-subtitle>
              1,000 miles of wonder
            </v-card-subtitle>

            <v-card-actions>
              <v-btn text>Share</v-btn>

              <v-btn
                color="purple"
                text
              >
                Explore
              </v-btn>

              <v-spacer></v-spacer>

              <v-btn
                icon
                @click="show = !show"
              >
                <v-icon>{{ show ? 'mdi-chevron-up' : 'mdi-chevron-down' }}</v-icon>
              </v-btn>
            </v-card-actions>

            <v-expand-transition>
              <div v-show="show">
                <v-divider></v-divider>

                <v-card-text>
                  I'm a thing. But, like most politicians, he promised more than he could deliver. You won't have time for sleeping, soldier, not with all the bed making you'll be doing. Then we'll go with that data file! Hey, you add a one and two zeros to that or we walk! You're going to do his laundry? I've got to find a way to escape.
                </v-card-text>
              </div>
            </v-expand-transition>
          </v-card>
        </v-flex>
      </v-layout>
    </v-container>
  </div>
</template>
