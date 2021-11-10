<template>
    <p>{{title}}</p>
</template>

<script>
import { ref } from "vue";
export default {
  components: {
  },
  props:{
      title:String
  },
    data(){
      return{
      }
  },
  setup(props) {
    console.log(props.title)
  }
}
</script>