<template>
        <div class="columns">
                <div class="column is-4 is-offset-1 "> 
                    <img  :src="'/img/robotron-' + (corRobotron) + '.png'" alt="Robotron">   
                </div>
                <div class="column is-2 text-center">
                    <div class="box">
                         <div class="estatistica">
                            <p class="estatistica-titulo">Força</p>
                            <div class="estatistica-valor">
                                <p class="estatistica-numero">{{forca}}</p>
                            </div>
                        </div>
                        <div class="estatistica">
                            <p class="estatistica-titulo">Poder</p>
                            <div class="estatistica-valor">
                                <p class="estatistica-numero">{{poder}}</p>
                            </div>
                        </div>
                        <div class="estatistica">
                            <p class="estatistica-titulo">Energia</p>
                            <div class="estatistica-valor">
                                <p class="estatistica-numero">{{energia}}</p>
                            </div>
                        </div>
                        <div class="estatistica">
                            <p class="estatistica-titulo">Velocidade</p>
                            <div class="estatistica-valor">
                                <p class="estatistica-numero">{{velocidade}}</p>
                            </div>
                        </div>
                    </div>                       
                </div>
                <div class="column is-4  text-center">
                    <div class="box">
                        <form action="">
                            <div>
                                <div class="peca">
                                    <label for="" class="peca-titulo">Braços</label>
                                    <div class="is-flex">                                        
                                        <buttom class="button is-danger is-light" @click="subtrair('braco')">-</buttom>
                                        <input type="text" class="input is-primary text-center" :value="braco" id="braco">
                                        <buttom class="button is-success is-light" @click="somar('braco')">+</buttom>
                                    </div>
                                </div>
                                <hr class="linha">
                                <div class="peca">
                                    <label for="" class="peca-titulo">Blindagem</label>
                                    <div class="is-flex">
                                        <buttom class="button is-danger is-light" @click="subtrair('blindagem')">-</buttom>
                                        <input type="text" class="input is-primary text-center" :value="blindagem" id="blindagem">
                                        <buttom class="button is-success is-light" @click="somar('blindagem')">+</buttom>
                                    </div>
                                </div>
                                <hr class="linha">
                                <div class="peca">
                                    <label for="" class="peca-titulo">Núcleos</label>
                                    <div class="is-flex">
                                        <buttom class="button is-danger is-light" @click="subtrair('nucleos')">-</buttom>
                                        <input type="text" class="input is-primary text-center" :value="nucleos" id="nucleos">
                                        <buttom class="button is-success is-light" @click="somar('nucleos')">+</buttom>
                                    </div>
                                </div>
                                <hr class="linha">
                                <div class="peca">
                                    <label for="" class="peca-titulo">Pernas</label>
                                    <div class="is-flex">
                                        <buttom class="button is-danger is-light" @click="subtrair('pernas')">-</buttom>
                                        <input type="text" class="input is-primary text-center" :value="pernas" id="pernas">
                                        <buttom class="button is-success is-light" @click="somar('pernas')">+</buttom>
                                    </div>
                                </div>
                                <hr class="linha">
                                <div class="peca">
                                    <label for="" class="peca-titulo">Foguetes</label>
                                    <div class="is-flex">
                                        <buttom class="button is-danger is-light" @click="subtrair('foguetes')">-</buttom>
                                        <input type="text" class="input is-primary text-center" :value="foguetes" id="foguetes">
                                        <buttom class="button is-success is-light" @click="somar('foguetes')">+</buttom>
                                    </div>
                                </div>
                                <hr class="linha">
                                <label for="color" class="peca-titulo">Escolha a color:</label>
                                <div>
                                    <select @click="color($event)" class='form-select' name="color" id="color">
                                        <option value="amarelo">Amarelo</option>
                                        <option value="azul">Azul</option>
                                        <option value="branco">Branco</option>
                                        <option value="preto">Preto</option>
                                        <option value="rosa">Rosa</option>
                                        <option value="vermelho">Vermelho</option>
                                    </select>
                                </div>                    
                            </div>
                            <input type="submit" value="Iniciar produção" class="button is-danger is-rounded" id="producao" style="margin-top:15px">
                        </form>
                    </div>
                    </div>
                </div>
</template>

<script>
export default {
    name:'RoboTron',
    data() {
        return{
            corRobotron: "amarelo",

            braco : 0,
            blindagem : 0,
            nucleos : 0,
            pernas : 0,
            foguetes : 0,

            forca : 773,
            poder : 630,
            energia : 289,
            velocidade: 597,

            adicional : {
                "braco": {
                    "forca": 29,
                    "poder": 35,
                    "energia": -21,
                    "velocidade": -5
                },

                "blindagem": {
                    "forca": 41,
                    "poder": 20,
                    "energia": 0,
                    "velocidade": -20
                },
                "nucleos":{
                    "forca": 0,
                    "poder": 7,
                    "energia": 48,
                    "velocidade": -24
                },
                "pernas":{
                    "forca": 27,
                    "poder": 21,
                    "energia": -32,
                    "velocidade": 42
                },
                "foguetes":{
                    "forca": 0,
                    "poder": 28,
                    "energia": 0,
                    "velocidade": -2
                }
                
            }
            } 
                               
        },
        
    methods: {
        color(e) {
            this.corRobotron = document.getElementById('color').value;
       },
        subtrair(partName) {
            //const partName = e.target.parentElement.childNodes[1].id            
            if (this[partName] > 0){
                this[partName] -= 1
                this.forca = this.forca - this.adicional[partName]['forca']
                this.poder = this.poder - this.adicional[partName]['poder']
                this.energia = this.energia - this.adicional[partName]['energia']
                this.velocidade = this.velocidade -  this.adicional[partName]['velocidade']
            }

                                    
       },
        somar(partName){        
            //const partName = e.target.parentElement.childNodes[1].id
            this[partName] += 1     
            this.forca = this.forca + this.adicional[partName]['forca']
            this.poder = this.poder + this.adicional[partName]['poder']
            this.energia = this.energia + this.adicional[partName]['energia']
            this.velocidade = this.velocidade + this.adicional[partName]['velocidade']        
       },
     
    }
}
    

</script>

<style scoped>
.form-select {
  display: block;
  width: 100%;
  padding: 0.375rem 2.25rem 0.375rem 0.75rem;
  -moz-padding-start: calc(0.75rem - 3px);
  font-size: 1rem;
  font-weight: 400;
  line-height: 1.5;
  color: #212529;
  background-color: #fff;
  background-image: url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 16 16'%3e%3cpath fill='none' stroke='%23343a40' stroke-linecap='round' stroke-linejoin='round' stroke-width='2' d='m2 5 6 6 6-6'/%3e%3c/svg%3e");
  background-repeat: no-repeat;
  background-position: right 0.75rem center;
  background-size: 16px 12px;
  border: 1px solid #ced4da;
  border-radius: 0.375rem;
  transition: border-color 0.15s ease-in-out, box-shadow 0.15s ease-in-out;
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
}
@media (prefers-reduced-motion: reduce) {
  .form-select {
    transition: none;
  }
}
.form-select:focus {
  border-color: #86b7fe;
  outline: 0;
  box-shadow: 0 0 0 0.25rem rgba(13, 110, 253, 0.25);
}
.form-select[multiple], .form-select[size]:not([size="1"]) {
  padding-right: 0.75rem;
  background-image: none;
}
.form-select:disabled {
  background-color: #e9ecef;
}
.form-select:-moz-focusring {
  color: transparent;
  text-shadow: 0 0 0 #212529;
}
</style>
