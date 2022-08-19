<template>
  <div>
  <CalcImc  />
  </div>
</template>

<script>
// @ is an alias to /src

import CalcImc from '@/components/CalcImc.vue';

export default {
  name: 'HomeView',
  components: {
    CalcImc,
    
}
}
</script>
