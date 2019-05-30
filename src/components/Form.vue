<template>
  <v-layout row justify-center>
    <v-dialog v-model="dialog" persistent max-width="1000px">
      <template v-slot:activator="{ on }">
        <v-btn color="primary" dark v-on="on">Register</v-btn>
      </template>



      
      <v-card height=700px tile=true>
        <!-- Heading of form -->
        <v-card-title>
          <span class="headline">Waves 2019 Registration</span>
        </v-card-title>
      <!-- End of Heading -->


      <!-- Beginning of Form -->
      <v-form v-model="valid">
        <v-card-text>
          <v-container grid-list-md>
            <v-layout wrap class="layout-class">

              <!-- First Name -->
              <v-flex xs12 sm6 md4>
                <v-text-field
                label="First name*"
                required
                :rules="firstNameRules"
                outline
                ></v-text-field>
              </v-flex>
              <!-- End of First Name -->


              <!-- Middle Name -->
              <v-flex xs12 sm6 md4>
                <v-text-field
                label="Middle name"
                outline
                ></v-text-field>
              </v-flex>
              <!-- End of Middle Name -->


              <!-- Last Name -->
              <v-flex xs12 sm6 md4>
                <v-text-field
                  label="Last name*"
                  required
                  :rules="lastNameRules"
                  outline
                ></v-text-field>
              </v-flex>
              <!-- End of Last Name -->


              <!-- Gender -->
              <v-flex xs12 sm6>
                <v-select
                  :items="['Male', 'Female']"
                  label="Gender*"
                  required
                  :rules="genderRules"
                  outline
                  ></v-select>
              </v-flex>
              <!-- End of Gender -->



              <!-- College Name -->
              <v-flex xs12 sm12>
                <v-text-field
                  label="Name of College*"
                  required 
                  outline
                  :rules="collegeRules"
                  ></v-text-field>
              </v-flex>
              <!-- End of College Name -->




              <!-- Events Participating -->
              <v-flex xs12 sm12>
                <v-autocomplete
                  :items="['FashP', 'Sizzle', 'Searock']"
                  label="Events Participating"
                  multiple
                  outline
                  required
                  :rules="eventRules"
                ></v-autocomplete>
              </v-flex>
              <!-- End of Events Participating -->



              <!-- Email -->
              <v-flex xs12>
                <v-text-field
                label="Email*"
                required
                :rules="emailRules"
                outline
                ></v-text-field>
              </v-flex>
              <!-- End of Email -->



              <!-- Phone Number -->
              <v-flex xs12 sm6>
                <v-text-field
                label="Phone Number*"
                required
                :rules="numberRules"
                @keypress="onlyNumber"
                outline
                ></v-text-field>
              </v-flex>



              
            </v-layout>
          </v-container>
          <p class="bottom-text" >*indicates required field</p>
        </v-card-text>
        </v-form>



        <v-card-actions class="bottom-card">
          <v-spacer></v-spacer>
          <v-btn color="blue darken-1" flat @click="dialog = false">Back</v-btn>
          <v-btn :disabled="!valid" color="blue darken-1" flat @click="dialog=false">Register</v-btn>
        </v-card-actions>



      </v-card>
    </v-dialog>
  </v-layout>
</template>





<script>

  export default {
    name : 'Form',
    data: () => ({
      dialog: false, 
      valid: false,


      firstNameRules: [
        v => !!v || 'First Name is required'

      ],

      lastNameRules: [
        v => !!v || 'Last Name is required'

      ],

      genderRules: [
         v => !!v || 'Gender is required'
      ],

      numberRules: [
        v => !!v || 'Phone Number is required',
        v => v.length == 10 || 'Phone Number should be 10 digits'

      ],

      collegeRules: [
        v => !!v || 'Name of College is required',

      ],



      emailRules: [
      v => !!v || 'E-mail is required',
      v => /.+@.+/.test(v) || 'E-mail must be valid'
      ],

      eventRules: [
        v => !!v || 'Events is required',
      ],



  

      
      

    }),

    methods : {

      onlyNumber ($event) {
        //console.log($event.keyCode); //keyCodes value
        let keyCode = ($event.keyCode ? $event.keyCode : $event.which);
        if ((keyCode < 48 || keyCode > 57) && keyCode !== 46) { // 46 is dot
          $event.preventDefault();
        }
      },

      // disable () {
      //   valid = false;  

      // },



    }

    
  }
</script>   


<style>
.bottom-card {
  height : 5px;
}



</style>
