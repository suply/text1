<template>
  <div>
    <div class="cell"  @click="OnClickMe">
        <template v-if="a">{{text}}</template>
        <template v-else></template>
     </div>
  </div>
</template>

<script>
export default {
    props:["n"],
    data () {
      return {a :false,text:""}
    },

    methods:{
        OnClickMe(){
          if (this.text!=="") {
            return;
          } 
            this.a = true;
            this.text=this.n%2===0?"X":"O";
            this.$emit("click",this.text);
        }
    }
  }
</script>
  
<style>
.cell {
  border:2px solid black;
  width: 100px;
  height: 100px;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 100px;
}
</style>
