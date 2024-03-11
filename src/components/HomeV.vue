<template>
  <div>Fullname: {{ fullName }}</div>
</template>

<script>
import { ref, computed } from "vue";

export default {
  setup() {
   const firstname = ref('Bethsy');
   const lastname = ref('Falcon')

   const fullName = computed(()=>{
    return `${firstname.value} ${lastname.value}`;
   })
   

    return {
      fullName
    };
  },
};
</script>