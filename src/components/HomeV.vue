<template>
  <div>{{ fullName }}</div>
  <div>{{ userName }}</div>
  <button ref="btn">Click!</button>
</template>

<script>
import { ref, toRefs, computed, inject, watch } from "vue";

export default {
  props: {
    firstName: String,
    lastName: String,
  },
  setup(props, { expose }) {
    const { firstName, lastName } = toRefs(props);

    const fullName = computed(() => {
      return `${firstName.value} ${lastName.value}`;
    });

    const userName = inject("userName")

    expose({
      fullName
    });

    const btn = ref(null)

   watch(btn, (valor)=>{
    console.log(valor)
   })

    return {
      fullName,
      userName,
      btn,
    };
  },
};
</script>