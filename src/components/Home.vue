<template>
  <main>
    <br/>
    <v-container fluid ma-0 pa-0 fill-height>
      <v-layout column align-center>
        <blockquote>
          &#8220;Welcome {{validUserName}}!&#8221;
          <footer>
            <small>
              <em>Eagle Financial Services, your Midwest Financial Services Partner.</em>
            </small>
          </footer>
        </blockquote>

      </v-layout>
    </v-container>
    <br/> <br/> <br/>

    <v-container grid-list-lg>
      <v-layout>
        <v-flex xs4>
          <v-card hover>
            <v-img
              :src="require('@/assets/images/customer.jpg')" height="200px">
            </v-img>
          <v-card-title>Customers</v-card-title>
          <v-card-actions>
            <v-btn color="error" @click="viewCustomers">View Details</v-btn>
          </v-card-actions>
          </v-card>
        </v-flex>

                <v-flex xs4>
                  <v-card hover>
                    <v-img
                      :src="require('@/assets/images/nonstock.jpg')" height="200px">
                    </v-img>
                    <v-card-title>Investments</v-card-title>

                    <v-card-actions>
                      <v-btn color="error" @click="viewInvestments">View Details</v-btn>
                    </v-card-actions>
                  </v-card>
                </v-flex>
                <v-flex xs4>
                  <v-card hover>
                    <v-img
                      :src="require('@/assets/images/stocks.jpg')" height="200px">
                    </v-img>
                    <v-card-title align-center>Stocks</v-card-title>

                    <v-card-actions>
                      <v-btn color="error" @click="viewStocks">View Details</v-btn>
                    </v-card-actions>
                  </v-card>
                </v-flex>
      </v-layout>
    </v-container>
  </main>
  </template>

<script>
  import router from '../router';

  export default {
    name: 'Home',
    data: () => ({
      validUserName: "Guest"
    }),
    mounted() {
      this.getUser();
    },
    methods: {
      viewCustomers() {
        router.push('/customer-list');
      },
      
      viewInvestments() {
        router.push('/investment-list');
      },

      viewStocks() {
        router.push('/stock-list');
      },
      
      getUser() {
        if (localStorage.getItem("isAuthenticates")
          && JSON.parse(localStorage.getItem("isAuthenticates")) === true) {
          this.validUserName = JSON.parse(localStorage.getItem("log_user"));
        }
      }
    }
  }
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
footer {
  position: fixed;
  left: 0;
  bottom: 0;
  width: 100%;
  background-color:rgb(0, 153, 255);
  color: rgb(253, 250, 250);
  text-align: center;
}
</style>