<template>
  <table class="calculette">
    <ecran :val="this.val" />
    <clavier @clicked="hundle" />
  </table>
</template>

<script>
import ecran from './components/ecran.vue'
import clavier from './components/clavier.vue'
import { onDeactivated } from '@vue/runtime-core'

export default {
  components: {
    ecran,
    clavier
  },
  data(){
    return {
      val:'',
      
    }
  },
  methods:{
    hundle(v){
      
      this.val=v;
      console.log(this.val)
    },

  }

}

</script>

<style>
#app {
    margin: 0;
    padding: 0;
    background: gray;
    box-sizing: border-box;
    width: min-content;
}


</style>
