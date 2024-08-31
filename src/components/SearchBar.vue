<template>
  <div class="relative">
    <input 
      v-model="query" 
      @input="fetchResults" 
      class="form-input mt-1 block w-full" 
      type="text" 
      placeholder="Search for clothing..."
    />
    <ul v-if="results.length" class="absolute bg-white border w-full mt-1">
      <li v-for="item in results" :key="item.id" class="p-2">
        {{ item.name }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      query: '',
      results: []
    };
  },
  methods: {
    fetchResults() {
      if (this.query.length > 3) {
        // Simulating an API call
        this.results = this.mockResults(this.query);
      } else {
        this.results = [];
      }
    },
    mockResults(query) {
      const items = [
         { id: 1, name: 'T-shirt' },
    { id: 2, name: 'Jeans'},
    { id: 3, name: 'Jacket' },
    { id: 4, name: 'Shirt' },
    { id: 5, name: 'girls-top' },
    { id: 6, name: 'jeans'},
    { id: 7, name: 'jacket' },
    { id: 8, name: 'tshirt' }
      ];
      return items.filter(item => item.name.toLowerCase().includes(query.toLowerCase()));
    }
  }
};
</script>

<style>
/* Add your styling here */
</style>
