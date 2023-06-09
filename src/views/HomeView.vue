<template>
  <div class="home">
    <SplashscreenComp/>
  </div>
  <div>
    <MyMapComp/>
  </div>
</template>

<script>
import SplashscreenComp from '@/components/SplashscreenComp.vue';
import MyMapComp from '@/components/MyMapComp.vue';

// @ is an alias to /src

export default {
  name: 'HomeView',
  components: {
    SplashscreenComp,
    MyMapComp
}
}
</script>
