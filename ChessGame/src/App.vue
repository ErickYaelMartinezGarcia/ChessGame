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
        ['','','','','','','',''],
        ['bP','bP','bP','bP','bP','bP','bP','bP'],
        ['bT','bH','bB','bK','bQ','bB','bH','bT'],
      ],
    };
  },
  methods: {
   getOddCells(i,rI){
      if(rI == 1 ||rI == 3||rI == 5||rI == 7){
        return (i)%2 === 0
      }
   return (i+1)%2 === 0
   },
   printFigure(str){
    
        let color = str.startsWith('w')
       if(color){
        switch(str){
            case 'wT': 
              return 'fa-regular fa-chess-rook bg-white rounded p-1';
            case 'wH': 
              return 'fa-regular fa-chess-knight bg-white rounded p-1';
            case 'wB': 
              return 'fa-regular fa-chess-bishop bg-white rounded p-1';
              case 'wK':
              return 'fa-regular fa-chess-king bg-white rounded p-1';
            case 'wQ': 
              return 'fa-regular fa-chess-queen bg-white rounded p-1';
            case 'wP': 
              return 'fa-regular fa-chess-pawn bg-white rounded p-1';
            }
       }

       switch(str){
            case 'bT': 
              return 'fa-solid fa-chess-rook';
            case 'bH': 
              return 'fa-solid fa-chess-knight';
            case 'bB': 
              return 'fa-solid fa-chess-bishop';
            case 'bK':
              return 'fa-solid fa-chess-king';
            case 'bQ': 
              return 'fa-solid fa-chess-queen';
            case 'bP': 
              return 'fa-solid fa-chess-pawn';
            }

       
    },

    moveFigure(pza,...coordinates){
      if(pza.endsWith('P')){
        debugger
        console.log(this.cells[coordinates[0]])
        console.log(coordinates[0])
        this.cells[coordinates[0]][coordinates[1]] = ''
        this.cells[coordinates[0]+1][coordinates[1]] = pza
        console.log(this.cells)
      }
    },
    movePawn(coordinates){
        //get and return new coordinates [column,row] 
        //evaluate if have some to eat
        return [coordinates[0+1],coordinates[1]]
    }
  },
  mounted() {
    
  },
};
</script>

<template>
  <div class=" col-8  border-dark border rounded-3 mx-auto" style="height:88vh" >
  <table class="col-12 h-100 rounded-3">
  <template v-for="(column,cI) in cells" :key="cI">
  <tr class=" row p-0 m-0" style="height:12.5%">
      <template v-for="(row,rI) in column" :key="rI">
            <td class=" col" :style="{ 'background-color': getOddCells(rI, cI) ? 'white' : 'grey' }">
              <div class="d-flex justify-content-center align-items-center h-100">
                <span class="fs-1" :class="printFigure(row)" @click="moveFigure(row,cI,rI)"></span>
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
