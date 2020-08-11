<template>
  <div class="box">
    <div class="button" @click="button">再来一局</div>
    <div class="result">第{{n}}步棋</div>
    <div class="chess">
    <div class="row">
      <Cell @click="onClickCell(0,$event)" :n="n"/>
      <Cell @click="onClickCell(1,$event)" :n="n"/>
      <Cell @click="onClickCell(2,$event)" :n="n"/>
    </div>
    <div class="row">
      <Cell @click="onClickCell(3,$event)" :n="n"/>
      <Cell @click="onClickCell(4,$event)" :n="n"/>
      <Cell @click="onClickCell(5,$event)" :n="n"/>
    </div>
    <div class="row">
      <Cell @click="onClickCell(6,$event)" :n="n"/>
      <Cell @click="onClickCell(7,$event)" :n="n"/>
      <Cell @click="onClickCell(8,$event)" :n="n"/>
    </div>
    </div>
    <div class="result">{{result===null ? '角逐中.........':`胜负已定！${result}获胜`}}</div>
  </div>
</template>

<script>
import Cell from './cell'
  export default {
    components:{ Cell },
    data(){
      return { n:0,
      map:[
        [null,null,null],
        [null,null,null],
        [null,null,null]
       ],
      result:null
      };
    },
 methods:{
   button(){
     window.location.reload()
   },
   onClickCell(i,text) {
     console.log(`${i}被点击了,内容为：${text}`);
     this.map[Math.floor(i/3)][i%3] = text;
     this.n=this.n+1;
     this.tell();
   },
   tell(){
     const map=this.map;
     for(let i=0;i<2;i++){
      if (map[i][0]!== null&&
      map[i][0]===map[i][1]&&
      map[i][1]===map[i][2]) {
        this.result=map[i][0];
      }
     }
     for(let j=0;j<2;j++){
      if (map[0][j]!== null&&
      map[0][j]===map[1][j]&&
      map[1][j]===map[2][j]) {
        this.result=map[0][j];
   }
}
      if (map[0][0]!== null&&
      map[0][0]===map[1][1]&&
      map[1][1]===map[2][2]) {
        this.result=map[0][0];
  }
      if (map[0][2]!== null&&
      map[0][2]===map[1][1]&&
      map[1][1]===map[2][0]) {
        this.result=map[0][2];
      }
      if (map[0][2]!== null&&
      map[0][2]===map[1][2]&&
      map[1][2]===map[2][2]) {
        this.result=map[0][2];
      }
      if (map[2][0]!== null&&
      map[2][0]===map[2][1]&&
      map[2][1]===map[2][2]) {
        this.result=map[2][0];
      }
   }
  }
}
</script>
  
<style>
.row{
  display: flex;
}
.box{
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
.result{
  font-size: 50px;
}
.button{
    font-size: 0.9em;
    color: #fff;
    background-color: #4fc08d;
    box-sizing: border-box;
    border: 1px solid #4fc08d;
    width: 200px;
    text-align: center;
    padding: 12px 24px;
    vertical-align: middle;
}
</style>
