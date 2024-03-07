<template>
    <div>{{ user }} Repositories</div>
  </template>
  
  <script>
  export default {
    props: {
      user: {
        type: String,
        required: true,
      },
    },
  
    
    computed: {
      filteredRepositories() {
        // 3
        return null;
      },
      repositoriesMatchingSearchQuery() {
        // 2
        return null;
      },
    },
  };
  </script>