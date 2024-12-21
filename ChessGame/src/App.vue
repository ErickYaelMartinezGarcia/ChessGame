<script>
//import HelloWorld from './components/HelloWorld.vue'
export default {
  components: {},
  data() {
    return {
      cells:[
        ['wT','wH','wB','wK','wQ','wB','wH','wT'],
        ['wP','wP','wP','wP','wP','wP','wP','wP'],
        ['','','','','','','',''],
        ['','','','','','','',''],
        ['','','','','','','',''],
        ['bP','bP','bP','bP','bP','bP','bP','bP'],
        ['bT','bH','bB','bK','bQ','bB','bH','bT'],
      ],
    };
  },
  methods: {
   getOddCells(i,rI){
      if(rI == 1 ||rI == 3||rI == 5||rI == 7){
        return (i+1)%2 === 0
      }
   return i%2 === 0
   },
   printFigure(str){
        let color = str.startWith('w')
       if(color){
        switch(str){
            case 'wT': 
              return 'fa-solid fa-chess-rook' 
            }
       } 
       
    }
  },
  mounted() {
    
  },
};
</script>

<template>
  <div class=" col-9 bg-dark border-dark border rounded-3 mx-auto" style="height:88vh" >
  <table class="col-12 h-100 rounded-3">
  <template v-for="(row,rI) in cells" :key="rI">
  <tr class="border" style="height:12.5%">
      <template v-for="(column,cI) in row" :key="cI">
            <td class="border" :style="{ 'background-color': getOddCells(cI, rI) ? 'white' : 'grey' }">
              <div class="my-auto w-100 text-justify text-center">
              
                <span class="fs-1 fa-solid fa-chess-pawn"></span>
              </div>
            </td>
      </template>  
    </tr> 
  </template>  
    
  </table> 
  </div> 
</template>

<style scoped>

</style>
