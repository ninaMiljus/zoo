<template>
  <div>
    <h1>Animals</h1>
    <table class="table">
      <thead>
        <tr>
          <th>Species</th>
          <th>Name</th>
          <th>Date of birth</th>
          <th>&nbsp;</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(animal, key) in animals" :key="key">
          <td>{{ animal.species }}</td>
          <td>{{ animal.name }}</td>
          <td>{{ animal.dateOfBirth ? animal.dateOfBirth : 'Nepoznat' }}</td>
        <td class="text-right">
        <button class="btn btn-danger btn-sm" @click="remove(animal)">Remove</button>
          <button class="btn btn-default btn-sm" @click="moveToTop(animal)">Move to top</button>
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
    return {
      animals: [
        {
          species: 'Dog',
          name: 'Dzeki',
          dateOfBirth: ''
        },
        {
          species: 'Cat',
          name: 'Cile',
          dateOfBirth: ''
        },
        {
          species: 'Parot',
          name: 'Zuti',
          dateOfBirth: '24-02-2015'
        },
        {
          species: 'Fish',
          name: 'Zlatna',
          dateOfBirth: '08-08-2016'
        },
        {
          species: 'Horse',
          name: 'Ridji',
          dateOfBirth: '12-09-2009'
        }
      ]
    };
  },
        methods: {
            remove(animal) {
            const index = this.animals.indexOf(animal);
                this.animals.splice(index, 1);
            },
        moveToTop(animal) {
        this.remove(animal);
        this.animals.unshift(animal);
                }
        }
};
</script>