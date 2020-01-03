<template>
  <card class="card" title="Permuter Etudiants">
    <div>
      <form  action="http://127.0.0.1:8081/table-list" method="post">



        <div class="row">

          <div class="col-md-4">

            <fg-input type="text"
                      label="Etudiant 1" 
                      placeholder="Entrez le matricule"
                      v-model="etudiant.first">
            </fg-input>
          </div>
          <div class="col-md-2">

          </div>
          <div class="col-md-4">

            <fg-input type="text"
                      label="Etudiant 2"
                      placeholder="Entrez le matricule"
                      v-model="etudiant.second">
            </fg-input>
          </div>
        </div>
       

        <div class="text-center">
          <p-button type="info"
                    round
                    @click.native.prevent="switchStudents">
           <!--Change-->
            Permuter
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
      etudiant: {
        first: "",
        second:""
      }
    };
  },
  methods: {
    switchStudents() {
      //axios.post('http://127.0.0.1:8000/api/permut', this.student);
      if (this.etudiant.first) {
        if (this.etudiant.second) {
          alert("Les deux étudiants : " + JSON.stringify(this.etudiant.first) + " and " + JSON.stringify(this.etudiant.second) + " ont été permuté avec success!");
          axios.post('http://127.0.0.1:8000/api/permutEtd', this.etudiant)
            .then(res => { console.log(res); })
          .catch(err => { console.log(err);})
        } else { alert("Remplissez les champs!");}
      }else { alert("Remplissez les champs!");}
    }
  }
};
</script>
