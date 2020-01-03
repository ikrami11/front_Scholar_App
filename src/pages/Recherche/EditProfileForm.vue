<template>
  <card class="card" title="Rechercher un étudiant par son matricule">
    <div>
      <form @submit.prevent>
        
        <div class="row">
          <div class="col-md-12">
            <fg-input type="text"
                      label="Matricule"
                      placeholder="12345"
                      v-model="user.address">
            </fg-input>
          </div>
        </div>

        <div class="text-center">
          <p-button type="info"
                    round
                    @click.native.prevent="updateProfile">
            Lancer la recherche
          </p-button>
        </div>
        <div class="clearfix"></div>
      </form>
    </div>
  </card>
</template>
<script>

import axios from 'axios';

export default {
  data() {
    return {
      user: {
        
      sont : "",
        
      }
    };
  },
  methods: {
    updateProfile() {
      axios.post('http://127.0.0.1:10080/api/rechmat', this.sont);
      alert("Les données de l'étudiant : " + JSON.stringify(this.user));
    }
  }
};
</script>
<style>
</style>
