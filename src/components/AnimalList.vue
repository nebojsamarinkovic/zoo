<template>
  <div class="hello">
    <table>
      <caption>Zivotinje u Zoo vrtu</caption>
      <tr>
        <th></th>
        <th></th>
        <th>Vrsta Zivotinje</th>
        <th>Ime</th>
        <th>Datum Rodjenja</th>
      </tr>
      <tr v-for="(zivotinja, index) in listaZivotinja" :key="index">
        <th><button @click="moveToTop(index, zivotinja)">Move to top</button></th>
        <td><button @click="removeAnimal(index)">Remove</button></td>
        <td>{{zivotinja.type}}</td>
        <td>{{zivotinja.name}}</td>
        <td v-if="zivotinja.dateOfBirth">{{zivotinja.dateOfBirth.toLocaleString()}}</td>
        <td v-else>Nepoznato</td>
      </tr>
    </table>
    
  </div>
</template>

<script>
export default {
  name: 'AnimalList',
  data () {
    return {
    listaZivotinja : [
      {name: "Vuk", type: "Divlja", dateOfBirth: new Date(2012, 0, 13)},
      {name: "Magarac", type: "Domaca", dateOfBirth: new Date(2008, 6, 23)},
      {name: "Soko", type: "Ptica", dateOfBirth: new Date(2016, 2, 2)},
      {name: "Zmija", type: "Gmizavac", dateOfBirth: new Date(2017, 1, 1)},
      {name: "Pirana", type: "Riba", dateOfBirth: new Date(2016, 9, 21)},
      {name: "Muva", type: "Insekt",   }, 
    ]
    }
  },

  methods: {
    removeAnimal(index){
      this.listaZivotinja.splice(index, 1);
      console.log("tu sam");
    },

    moveToTop(index, zivotinja){
      this.listaZivotinja.splice(index, 1);
      this.listaZivotinja.unshift(zivotinja);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

table, th, td {
  border : 1px solid black;
  border-collapse: collapse;
}

th, td {
  padding: 10px;
}

</style>
