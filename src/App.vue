<script>

export default{
  name : 'App',
  data(){
    return {
        entrer : '',
        resultat : ''
    }
  },
  methods : {
     affichage(val){
        this.entrer = this.entrer + val 
     },
     calcule() {
        let entrer = this.entrer.replace(/sin\(/g, 'Math.sin(')
                                .replace(/cos\(/g, 'Math.cos(')
                                .replace(/tan\(/g, 'Math.tan(')
                                .replace(/PI/g, 'Math.PI')
                                .replace(/racine\(/g, 'Math.sqrt(')
                                .replace(/pow\(/g, 'Math.pow(');
        this.resultat = eval(entrer);
        this.entrer = this.resultat
      
     },
     effacer(){
        this.entrer = '',
        this.copy = []
     }
  }
}

</script>



<template>
    <body>
        <div class="corps">
            <form action="" @submit.prevent="calcule">
              <input type="text" v-model="entrer">
              <input class="sub" type="submit" value="=">
            </form>
            <div class="boutton">
              <div class="bout1">
                <div class="un">
                  <button @click="()=> affichage('1')" class="btn">1</button>
                  <button @click="()=> affichage('2')" class="btn">2</button>
                  <button @click="()=> affichage('3')" class="btn">3</button>
                  <button @click="()=> affichage('4')" class="btn">4</button>
                </div>
                <div class="deux">

                </div>          
                <div class="trois">
                  <button @click="()=> affichage('5')" class="btn" >5</button>
                  <button @click="()=> affichage('6')" class="btn" >6</button>
                  <button @click="()=> affichage('7')" class="btn" >7</button>
                  <button @click="()=> affichage('8')" class="btn" >8</button>
                </div>
                <div class="quatre">                
                  <button @click="()=> affichage('9')" class="btn">9</button>
                  <button @click="()=> affichage('.')" class="btn">.</button>
                  <button @click="()=> affichage('0')" class="btn">0</button>
                  <button @click="()=> affichage('PI')" class="btn">pi</button>
                </div>
                <div class="cinq">                
                  <button @click="()=> affichage('sin(')" class="btn" >sin</button>
                  <button @click="()=> affichage('cos(')" class="btn" >cos</button>
                  <button @click="()=> affichage('tan(')" class="btn" >tan</button>
                  <button @click="()=> affichage('pow(')"   class="btn" >pow</button>
                </div>
                <div class="six">                
                  <button @click="()=> affichage('(')"       class="btn" >(</button>
                  <button @click="()=> affichage(')')"       class="btn" >)</button>
                  <button @click="()=> affichage('%')"       class="btn" >%</button>
                  <button @click="()=> affichage('racine(')"  class="btn" >racine</button>
                </div>
              </div>
              <div class="bout2">
                <button @click="()=> affichage('+')" class="btn">+</button>
                <button @click="()=> affichage('-')" class="btn">-</button>
                <button @click="()=> affichage('/')" class="btn">/</button>
                <button @click="()=> affichage('*')" class="btn">x</button>
                <button @click="()=> effacer()" class="btn" id="clear">Clear</button>
              </div>
            </div>
            
        </div>
    </body>
</template>

<style lang="scss">
  %btn {
    width: 2.8cm;
    height: 1cm;
  }
  .sub{
      font-size: 28px;
      cursor: pointer;
    }
    #clear{
      background-color: #E8AA42;
    }
    input{
        height: 2cm;
        width: 100%;
    }
   body{
      background-color: #120b3a;
      margin: 0;
      padding: 0;
      width: 100%;
   } 
     .corps{
        background-color: rgb(49, 47, 47);
        width: 16cm;
        padding: 10px;
        margin-left: 8cm;
        box-shadow: 8px -2px 18px black;
        border-radius: 5px;
     }
     .boutton{
        width: 100%;
        display: flex;
        /* background-color: blue; */
        font-size: 12px;
     }
     button{
      font-size: 25px;
     }
     .bout1{
      padding-top: 5px;
      width: 12cm;
      background-color: rgb(193, 213, 219);
           button{
              background-color: #1F4690;
              color: aliceblue;
              border: none;
              border-radius: 2px;
              box-shadow: 2px 4px 5px black;
              &:hover{
                  background-color: #13326d;
                  cursor: pointer;        
                  box-shadow: 0px 0px 0px black;
              }
          }
        }
     .bout2{
        width: 3cm;
       .btn{
          width: 3.5cm;
          height: 1.2cm;
        }
     }
     .un{
      padding: 2px;
      display: flex;
      justify-content: space-around;
          .btn{
              @extend %btn;
          }
     }
     .deux{
        @extend .un;
     }
     .trois{
        @extend .un;
     }
     .quatre{
        @extend .un;
    }
    .cinq{
        @extend .un;
    }
    .six{
        @extend .un;
    }
</style>
