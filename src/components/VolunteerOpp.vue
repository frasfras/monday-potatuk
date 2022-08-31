<template>
  <v-form v-model="valid">
    <v-container>
      <h1 align="left">Climate change Volunteering Group</h1>
      <h1 align="left"></h1>
      <v-row>
        <v-col cols="4" sm="6" md="6">
          <v-slider
            v-model="fx9.val"
            :label="fx9.label"
            min="8"
            max="15"
            :color="fx9.color"
            thumb-label="always"
          ></v-slider>
        </v-col>
      </v-row>

      <v-row>
        <h3>
          Studies show that 100% of people who volunteer, will eventually be
          happy.
        </h3>
        <v-col cols="4" sm="6" md="6">
          <v-text-field v-model="url" label="monitor Feed" required>
          </v-text-field>
        </v-col>
        <v-col cols="4" sm="6" md="6">
          <v-img
            lazy-src="https://res.cloudinary.com/mermi/image/upload/v1592676978/PegaHackathon/Accenture_Facts_ljgegj.png"
            max-height="150"
            max-width="250"
            src="https://res.cloudinary.com/mermi/image/upload/v1592676978/PegaHackathon/Accenture_Facts_ljgegj.png"
          ></v-img>
        </v-col>
      </v-row>
      <v-row justify="space-around">
        <v-col cols="12" sm="6">
          <div class="span5 well">
            <form>
              <fieldset>
                <h3>Create new Volunteering opportunity using Boardview</h3>
                <legend>Volunteer Opportunity Login</legend>
                <label>Enter your account information</label>
                <v-form ref="form" v-model="valid" lazy-validation>
                  <v-row>
                    <v-col cols="12" md="12">
                      <v-text-field
                        v-model="board_id"
                        :counter="10"
                        :rules="nameRules"
                        label="enter board Id"
                        required
                      ></v-text-field>

                      <v-text-field
                        v-model="description"
                        :counter="10"
                        :rules="nameRules"
                        label="description of opportunity"
                        required
                      ></v-text-field>

                      <v-select
                        v-model="select"
                        :items="items"
                        label="category"
                      ></v-select>
                      <label class="checkbox">
                        <v-checkbox
                          v-model="checkbox"
                          :label="`Online: ${checkbox.toString()}`"
                        ></v-checkbox>
                      </label>
                      <label class="checkbox">
                        <v-checkbox
                          v-model="checkbox2"
                          :label="`Plant Tree: ${checkbox.toString()}`"
                        ></v-checkbox>
                      </label> </v-col
                  ></v-row>
                </v-form>
              </fieldset>
              <div class="text-center">
                <v-btn rounded color="primary" dark @click="AddOppurtunity"
                  >Add Climate action
                </v-btn>
              </div>
            </form>
            <div class="alert alert-success">
              <strong>Thank You for Climate offsetting!</strong>
            </div>
          </div>
        </v-col>
        <v-col class="d-flex" cols="12" sm="6">
          <div>
            <table id="demo-table-id" class="table table-striped">
              <caption>
                Volunteering opportunity
              </caption>
              <thead>
                <tr>
                  <th>Item #</th>
                  <th>Description</th>
                  <th></th>
                  <th>Carbon emission</th>
                  <th>Cost</th>
                  <th>Trees</th>
                  <th>Total</th>
                </tr>
              </thead>
              <tbody>
                <tr>
                  <td>1000</td>
                  <td>Turning waste biogas in Thailand.</td>
                  <td></td>
                  <td>10</td>
                  <td>1.00</td>
                  <td></td>
                  <td>$10.00</td>
                </tr>
                <tr>
                  <td>2000</td>
                  <td>Plant Trees in the Philippines</td>
                  <td></td>
                  <td>3</td>
                  <td>8.75</td>
                  <td></td>
                  <td>$26.25</td>
                </tr>
                <tr>
                  <td>3007</td>
                  <td>renewable solar energy in Egypt</td>
                  <td></td>
                  <td>5</td>
                  <td>7.50</td>
                  <td></td>
                  <td>$37.50</td>
                </tr>
                <tr class="info">
                  <td colspan="4"></td>
                  <td>
                    <b>$73.75</b>
                  </td>
                </tr>
              </tbody>
            </table>
          </div>
        </v-col>
      </v-row>
    </v-container>
  </v-form>
</template>

<script>
//import HelloWorld from "../components/PlanView";
//import HelloWorld from "../components/BnbDeal";
/* eslint-disable */ 
  export default {
    name: 'VolunteerOpp',

    components: {
  
    },
    props: {
    
    msg: String,
  },
  //component code
 
     data: () => ({
      valid: false,
      itemname: '',
      lastname: '',
      board_id: 2845184846,
      url: 'https://frans-77.fred.sensetecnic.com/api/monitor',
      checkbox: true,
      checkbox2: true,
      items: ['Multinationals group', 'Rights OF Nature', 'ecocide', ' education','De Climatologist','Biodiversity'],
      fx9: { label: "hours", val: 50, color: "#234560" },
      nameRules: [
        v => !!v || ' is required',
        v => v.length <= 50 || ' must be less than 50 characters',
      ],
      email: '',
      emailRules: [
        v => !!v || 'E-mail is required',
        v => /.+@.+/.test(v) || 'E-mail must be valid',
      ],
    }),
    methods: {
            
        AddOppurtunity() {
      var myHeaders = new Headers();
      
        var boardId = this.board_id;
        var item = this.itemname + ' ' + this.description;

        myHeaders.append("Authorization", "eyJhbGciOiJIUzI1NiJ9.eyJ0aWQiOjE3NzY3Mjg3MCwidWlkIjozMTU0NzE5NiwiaWFkIjoiMjAyMi0wOC0yNlQxNDoyOTo1Ni4wMDBaIiwicGVyIjoibWU6d3JpdGUiLCJhY3RpZCI6MTI1Nzg0NDIsInJnbiI6InVzZTEifQ.dJqhXVLdY1yvpl0x_yADidBgh19NLEZmMiunKQc3N40");
        myHeaders.append("Content-Type", "application/json");
        myHeaders.append("Cookie", "__cf_bm=mwVnwHh171Q7YxRp4Mqj7WoqwBepeDSNJmyT73kNWb8-1661741853-0-Ae1+PHNtWhKRCgi1sXYd2DONKnUkjuEZFpInPBsf0Lu5UoG/AR5rd53TrgnF2e2A4L1AR/P3Kk9825V2oaezod65SZ4VI4oQ8RLOR/n+ziSr");

        var graphql = JSON.stringify({
        query: "mutation myAdd($board_id: Int!,$item_name: String){\n  create_item(board_id: $board_id, item_name: $item_name){\n    id\n    name\n  }\n}",
        variables: {"item_name":item,"board_id":boardId}
        })
        var requestOptions = {
        method: 'POST',
        headers: myHeaders,
        body: graphql,
        redirect: 'follow'
        };

        fetch("https://api.monday.com/v2/", requestOptions)
        .then(response => response.text())
        .then(result => console.log(result))
        .catch(error => console.log('error', error));
            },

    }
  };
</script>
<style>
knob-label {
    display: block;
    margin-bottom: 0;
    font-weight: bold;
     color: #febc2c;
}
h1 {
   color: blue;
}
</style>