<template>
  <div>
    <h1>Animals</h1>
     <form v-on:submit.prevent="addAnimal">
      <div class="form-group">
        <label for="species">Species:</label>
        <input class="form-control" name="species" type="text" v-model="newAnimal.species"/>
      </div>

      <div class="form-group">
        <label for="name">Name:</label>
        <input class="form-control" name="name" type="text" v-model="newAnimal.name"/>
      </div>

      <div class="form-group">
        <label for="dateOfBirth">Date of birth:</label>
        <input class="form-control" name="dateOfBirth" type="text" v-model="newAnimal.dateOfBirth"/>
      </div>

      <div class="form-group">
        <select v-model="selected">
        <option v-for="(sector, index) in sectors" :key="index">{{sector}}</option>
      </select>
      </div>
        <button type="submit">Add animal</button>
       </form>
    <br/>
    <table class="table">
      <thead>
        <tr>
          <th>Species</th>
          <th>Name</th>
          <th>Date of birth</th>
          <th>Sector</th>
          <th>&nbsp;</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(animal, index) in animals" :key="animal.name">
          <td>{{ animal.species }}</td>
          <td>{{ animal.name }}</td>
          <td>{{ animal.dateOfBirth ? animal.dateOfBirth : 'Nepoznat' }}</td>
            <td>{{ animal.sector }}</td>
        <td class="text-right">
        <button class="btn btn-danger btn-sm" @click="remove(index)">Remove</button>
          <button class="btn btn-default btn-sm" @click="moveToTop(index)" v-if="index !== 0">Move to top</button>
        </td>
        </tr>
      </tbody>
    </table>
    <table class="table">
      <thead>
        <th>Sector</th>
        <th>&nbsp;</th>
      </thead>
      <tbody>
        <tr v-for="(sector, key) in sectors" :key="key">
          <td>{{ sector }}</td>
          <td class="text-right">
            <button class="btn btn-default btn-sm" @click="showAnimalsBySector(sector)">View list of animals</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>

export default {
  name: 'AnimalList',
  data() {
    const sectors = ['Vodene', 'Kopnene', 'Ptice'];
    return {
        sectors: sectors,
        selected: 'Sektor',
        newAnimalSpecies: '',
        newAnimalName: '',
        NewAnimalDateOfBirth: '',
      animals: [
        {
          species: 'Dog',
          name: 'Dzeki',
          dateOfBirth: '',
          sector: sectors[1]
        },
        {
          species: 'Cat',
          name: 'Cile',
          dateOfBirth: '',
           sector: sectors[1]
        },
        {
          species: 'Parot',
          name: 'Zuti',
          dateOfBirth: '24-02-2015',
           sector: sectors[2]
        },
        {
          species: 'Fish',
          name: 'Zlatna',
          dateOfBirth: '08-08-2016',
           sector: sectors[0]
        },
        {
          species: 'Horse',
          name: 'Ridji',
          dateOfBirth: '12-09-2009',
           sector: sectors[1]
        }
      ],
      newAnimal: {
         species: this.newAnimalSpecies,
         name: this.newAnimalName,
         dateOfBirth: this.NewAnimalDateOfBirth,
         sector: this.newAnimalSector
      }
    };
  },
        methods: {
            remove(index) {
                this.animals.splice(index, 1);
            },
            moveToTop(index) {
                let removed = this.animals(index);
                this.remove(index);
                this.animals.unshift(removed);
            },
            addAnimal() {
                this.animals.push(this.newAnimal);

                this.newAnimalSpecies = '';
                this.newAnimalName = '';
                this.NewAnimalDateOfBirth = '';
                
            },
            showAnimalsBySector(sector) {
                const animalsList=[];
                    this.animals.forEach(animal => {
                        if (animal.sector === sector) {
                        animalsList.push(`${animal.name}`);
                    }
                });
                alert(animalsList.toString());
            }
        }
};
</script>