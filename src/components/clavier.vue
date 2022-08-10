<template>
  <tr>
    <td><button class="btn sp" @click="calculer('sp', 'c')">c</button></td>
    <td><button class="btn sp" @click="calculer('sp', 'ce')">ce</button></td>
    <td><button class="btn sp" @click="calculer('op', '%')">%</button></td>
    <td><button class="btn sp" @click="calculer('op', '/')">/</button></td>
  </tr>
  <tr>
    <td><button class="btn" @click="calculer('ch', 7)">7</button></td>
    <td><button class="btn" @click="calculer('ch', 8)">8</button></td>
    <td><button class="btn" @click="calculer('ch', 9)">9</button></td>
    <td><button class="btn sp" @click="calculer('op', '*')">*</button></td>
  </tr>
  <tr>
    <td><button class="btn" @click="calculer('ch', 4)">4</button></td>
    <td><button class="btn" @click="calculer('ch', 5)">5</button></td>
    <td><button class="btn" @click="calculer('ch', 6)">6</button></td>
    <td><button class="btn sp" @click="calculer('op', '-')">-</button></td>
  </tr>
  <tr>
    <td><button class="btn" @click="calculer('ch', 1)">1</button></td>
    <td><button class="btn" @click="calculer('ch', 2)">2</button></td>
    <td><button class="btn" @click="calculer('ch', 3)">3</button></td>
    <td><button class="btn sp" @click="calculer('op', '+')">+</button></td>
  </tr>
  <tr>
    <td colspan="2">
      <button class="btn zero" @click="calculer('ch', 0)">0</button>
    </td>
    <td><button class="btn" @click="calculer('dec', '.')">.</button></td>
    <td><button class="btn" @click="calculer('eg', '=')">=</button></td>
  </tr>
</template>

<script>
export default {
  data() {
    return {
      cnt: 0,// the variable emited 
      oper: "",// wich operation 
      operate1: 0,// the result or the content after every operation 
    };
  },
  methods: {
    calculer(t, v) {
      switch (t) {
        case "ch":
          if (this.cnt == "0") this.cnt = "";
          this.cnt += v;
          break;
        case "op":
          if (this.oper != "") {
            var operate3 = parseFloat(this.cnt)
            var result1 = 0;
            switch (this.oper) {
              case "+":
                result1 = this.operate1 + operate3;
                break;
              case "-":
                result1 = this.operate1 - operate3;
                break;
              case "*":
                result1 = this.operate1 * operate3;
                break;
              case "/":
                if (operate2 == 0) {
                  this.cnt = "ERROR";
                  break;
                }
                result1 = this.operate1 / operate3;

                break;
              case "%":
                result1 = this.operate1 % operate3;
                break;
            }
            this.cnt = result1.toString();
          }
          this.oper = v;
          this.operate1 = parseFloat(this.cnt);
          this.cnt = "";
          console.log(this.oper);
          console.log(this.operate1);
          break;
        case "dec":
          if (this.cnt.indexOf(v) == -1) this.cnt += ".";
          break;
        case "eg":
          var operate2 = parseFloat(this.cnt);
          var result = 0;
          switch (this.oper) {
            case "+":
              result = this.operate1 + operate2;
              break;
            case "-":
              result = this.operate1 - operate2;
              break;
            case "*":
              result = this.operate1 * operate2;
              break;
            case "/":
              if (operate2 == 0) {
                this.cnt = "ERROR";
                break;
              }
              result = this.operate1 / operate2;

              break;
            case "%":
              result = this.operate1 % operate2;
              break;
          }
          this.cnt = result.toString();
          this.oper='';
          break;
        case "sp":
          switch(v){
            case 'c':
              this.cnt='';
              this.oper='',
              this.operate1=''
            break;
            case 'ce':
              if(this.cnt==''){
                this.oper='' ;
                this.cnt=this.operate1;
              } 
              else this.cnt = this.cnt.slice(0, -1);
            break;
          }
          break;
      }
      this.$emit("clicked", this.cnt);// emit cnt to app.vue to send it kike prop to ecran.vue 
    },
  },
};
</script>

<style>
.btn {
  width: 40px;
  height: 40px;
  background: black;
  color: aliceblue;
  border-radius: 5px;
  font-size: 1.5em;
}

.btn:hover {
  color: black;
  box-shadow: 4px rgb(133, 88, 52);
  background: rgb(59, 47, 70);
}
tr .zero {
  width: 100%;
}
.sp {
  border: 1px solid orangered;
  color: orangered;
  border-radius: 30%;
}

tr .sp:hover {
  background: orangered;
  border: 1px solid black;
  color: aliceblue;
  box-shadow: 4px rgb(133, 88, 52);
}
</style>
