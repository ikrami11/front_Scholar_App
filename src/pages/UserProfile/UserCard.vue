<template>
  <card class="card" title="Permuter Etudiants">
    <div>
      <form @submit.prevent>



        <div class="row">

          <div class="col-md-4">

            <fg-input type="text"
                      label="Etudiant 1" 
                      placeholder="Entrez le matricule"
                      v-model="student.first">
            </fg-input>
          </div>
          <div class="col-md-2">

          </div>
          <div class="col-md-4">

            <fg-input type="text"
                      label="Etudiant 2"
                      placeholder="Entrez le matricule"
                      v-model="student.second">
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
      student: {
        first: "",
        second:""
      }
    };
  },
  methods: {
    switchStudents() {
      axios.post('http://127.0.0.1:8000/api/permut', this.student);
      if (this.student.first) {
        if (this.student.second) {
          alert("Les deux étudiants : " + JSON.stringify(this.student.first) + " and " + JSON.stringify(this.student.second) + " ont été permuté avec success!");
          axios.post('http://127.0.0.1:8000/permutEtd', this.student);
        } else { alert("Remplissez les champs!");}
      }else { alert("Remplissez les champs!");}
    }
  }
};
</script>
