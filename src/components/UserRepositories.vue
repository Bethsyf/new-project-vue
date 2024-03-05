<template>
  <div>{{ user }} Repositories</div>  
</template>

<script>
export default {
    props: {
        user: {
            type: String,
            required: true,
        }
    }
}</script>