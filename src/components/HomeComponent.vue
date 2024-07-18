<template>
    
    <div>

    <section id="area-conteudo-principal">
      
      <div class="container">


        <div class="row">

        

         <div  class="col-md-6">
          

          <div id="carousell" class="carousel slide" data-bs-ride= "carousel">

            <div class="carousel-inner">
              <div class="carousel-item active">
                <img src="../assets/img/neymarblaze2.png" class="img-fluid"  alt="Slide 1">
              </div>

              <div class="carousel-item">
                <img src="../assets/img/neymarblaze.png" class="img-fluid" alt="Slide 2">
              </div>

              <div class="carousel-item">
                <img src="../assets/img/neymarblaze3.png" class="img-fluid" alt="Slide 2">
              </div>

            </div>

            <a class="carousel-control-prev" href="#carousell" data-bs-slide="prev">
              <span class="carousel-control-prev-icon"></span>
              
            </a>


            <a class="carousel-control-next" href="#carousell"  data-bs-slide="next">
              <span class="carousel-control-next-icon"></span>
              
            </a>
        </div>
          
          <div>
            
            <h2 class="neymar text-center font1">Neymar da Silva Santos Júnior</h2>

            <h4 class="text-center text-info-emphasis font" >Patrocinador Oficial Da PLAZE</h4>

          </div>

        </div>



        <div class="col-md-6 align-self-center">
          
          <h1 class="text-light">PLAZE</h1>

          <p class="text-light" style="font-size: 1.2em;">{{msg}}</p>


          <input :value="msgPlace" @keyup="pesquisarJogo" id="pesquisa-jogos" class="form-control text-center d-sm-block d-none custom" type="text" name="" placeholder="Pesquise o Nome do Jogo">

          
          
          <div class="row d-sm-block d-none">

            <div class="col-md-12 text-center">
              <a :href="link">
                 <img id="foto" v-if="imgAtivada" :src="require(`../assets/img/${img}`)">
              </a>
            </div>


          </div> 


        </div>


      </div>
        




        

      </div>


    </section>
    





  <div class="linear">
    <!---Segunda Sessao--->
    <section class="container">
      
      <h4 class="text-center ajuste text-uppercase font">Venha jogar os melhores jogos que estão em alta!🔥🔥🔥🔥</h4>

      <div id="segunda_sessao" class="row">

        <div class="col-md-12 text-center">

          

        </div>
        

        <div class="col-md-12 align-self-center">
          

          <div class="row hidden observe" :class="{show: exibir}">

            <div class="col-md-3">
              <img src="../assets/img/mines.png" class="img-fluid bg-dark p-3">
              <div class="d-grid">
              <a href="https://zdvictor.github.io/Projeto-MinesTower/" type="button" class="mt-2 btn btn-warning btn-lg">CLIQUE AQUI PARA JOGAR🔥</a>
             </div>
            </div>            
            
            <div class="col-md-3">
              <img src="../assets/img/foto6.jpg" class="img-fluid">
              <div class="d-grid">
              <a href="https://demofortunetiger.com/#demo" type="button" class="mt-2 btn btn-primary btn-lg">CLIQUE AQUI PARA JOGAR🔥</a>
             </div>
            </div>

            <div class="col-md-3">
              <img src="../assets/img/foto7.jpg" class="img-fluid">
              <div class="d-grid">
              <a href="https://demofortunerabbit.com/#demo" type="button" class="mt-2 btn btn-success btn-lg">CLIQUE AQUI PARA JOGAR🔥</a>
              </div>
            </div>

            <div  class="col-md-3">
              <img src="../assets/img/foto8.png" class="img-fluid">
              <div class="d-grid">
              <a href="https://fortuneoxdemo.com.br/#demo" type="button" class="mt-2 btn btn-secondary btn-lg">CLIQUE AQUI PARA JOGAR🔥</a>
              </div>
            </div>

          


          </div>



        </div>







      </div>


    </section>

    </div>

    <!---Terceira Sessao CHAT--->
    <section > 

        <div class="" :class="{'hidden-chat': chatDesativado, 'chat-responsive': !chatDesativado}">

          <button @click="ativarChat" class="btn  btn-danger chat-close">X</button>

          <div class="chat-adm">

            <h5 class="chat-adm-msg">🤖 Olá, tudo bem? Como posso ajudar? <br>
            
            <p class="lead">Digite:</p>

            <div class="chat-adm-msg-auto">

              1: Para jogos <br>
              2: Apostas esportivas <br>
              3: Afiliados 

            </div>

            </h5>

          </div>

          <div v-for="resposta in respostas" :key="resposta.id">

            <div v-if="resposta.cargo == 'user' ">

              <p class="bg-primary fs-4 text-end" >{{ resposta.msg }}</p>
             

            </div>

            <div v-else-if="resposta.cargo == 'adm'">
              
              <p class="bg-success fs-4 text-light" >{{ resposta.msg }}</p>

              
            </div>

          </div>

        <div class="chat-input">
          <input v-model="msgUsuario" type="text" class="form-control" placeholder="Digite Sua Mensagem Aqui">
          <div class="d-grid mt-2">
            <button @click="msgUser" class="btn btn-success">Enviar</button>
          </div>
          
        </div>


        </div>

        <!---<img class="chat-img" src="../assets/img/chat.png" alt="">-->
        <div @click="ativarChat" class="chat-img">💬</div>

    </section>


    </div>


</template>

<script>
export default {

      data() {

      return {

        msg: '',
        msgPlace: '',
        exibir: false,
        img: '',
        imgAtivada: false,
        link: '',
        chatDesativado: true,
        respostas: [],
        msgUsuario: ''




      }


    },


    methods:  {

     pesquisarJogo: function()  {



		let pesquisar = document.getElementById('pesquisa-jogos').value


  if (pesquisar === 'mines' || pesquisar === 'Mines' || pesquisar === 'MINES') {

      this.imgAtivada = true
      this.img = 'mines.png'
      this.link = 'https://zdvictor.github.io/Projeto-MinesTower/'


}


		if (pesquisar === 'tigre' || pesquisar === 'Tigre' || pesquisar === 'TIGRE') {

      this.imgAtivada = true
			this.img = 'foto6.jpg'
      this.link = 'https://demofortunetiger.com/#demo'
		

		}


		if (pesquisar === 'coelho' || pesquisar === 'Coelho' || pesquisar === 'COELHO') {


      this.imgAtivada = true
			this.img = 'foto7.jpg'
      this.link = 'https://demofortunerabbit.com/#demo'


		}

		if (pesquisar === 'touro' || pesquisar === 'Touro' || pesquisar === 'TOURO') {


      this.imgAtivada = true
			this.img = 'foto8.png'
      this.link = 'https://fortuneoxdemo.com.br/#demo'



		

		}

    if (pesquisar === '' || pesquisar === ' ' || pesquisar === null || pesquisar === undefined) {

      this.imgAtivada = false
			

		}



},

  ativarChat: function() {


      this.chatDesativado = !this.chatDesativado


  },

  msgResponseAdm: function(value) {

  setTimeout(() => {
    

  if(value == 1){

this.respostas.push({ id: Date.now(), cargo: "adm", msg: '🤖' + "Mais jogos serão adicionados em breve." });

return

} 

if(value == 2){

this.respostas.push({ id: Date.now(), cargo: "adm", msg: '🤖 ' + "Apostas esportivas em breve." });

return

} 

if(value == 3) {

this.respostas.push({ id: Date.now(), cargo: "adm", msg: '🤖 ' + "Sistema de afiliados em breve." });

return

}


else {

  this.respostas.push({ id: Date.now(), cargo: "adm", msg: '🤖 ' + "Ops, não entendi. Digite um dos números acima." });

  return

}

  },  700)


  },

  msgUser: function() {

    if (this.msgUsuario.trim() !== '') {

         this.respostas.push({ id: Date.now(), cargo: "user", msg: this.msgUsuario + ' ' + '👤' });
         this.msgResponseAdm(this.msgUsuario)
         this.msgUsuario = ''


         
               
  
          
  
    }

  }



    },

    mounted() {

        var myObserver = new IntersectionObserver(entries => {

        entries.forEach(entry => {
            if (entry.isIntersecting) {
                this.exibir = true
                console.log('Entrou')
            } else {
                this.exibir = false
                console.log('Saiu')
            }
        });
    });

    
        var itens = document.querySelectorAll(".observe");

    
        itens.forEach(item => {
        console.log(item);
        myObserver.observe(item);
});
      


    },

    created() {

  

      var mensagem = 'Participe da emoção na PLAZE: Faça suas apostas e tenha a chance de ganhar grandes prêmios em dinheiro!'
      var carachter = 0;

      var delay = 70

          const repeatLetter = () => {

            if(carachter < mensagem.length) {

              this.msg += mensagem[carachter]
              carachter++

              setTimeout(repeatLetter, delay)

            }
            

          }

        repeatLetter()

       var msgPlace = 'Exemplo: Mines,Tigre,Touro,Coelho'
       var carachterPlace = 0;

       var delayPlace = 70

          const repeatLetterPlace = () => {

            if(carachterPlace < msgPlace.length) {

              this.msgPlace += msgPlace[carachterPlace]
              carachterPlace++

              setTimeout(repeatLetterPlace, delayPlace)

            }
            

          }

          setTimeout( () => {

            repeatLetterPlace()

          }, 8000)

          setTimeout( () => {

            this.msgPlace = ''

          }, 14000)


    },


}
</script>

<style>

@media(max-width: 1100px) {


.chat-responsive{
  
  
  width: 100%;
  height: 100%;
  position: fixed;
  top: 0;
  background: #ccc;
  padding: 30px 20px;
  opacity: 1;
  filter: blur(0);
  transition: all 2s;
  overflow-y: auto;

}

  
}

@media(min-width: 1100px) {


.chat-responsive{
  
  
  width: 15%;
  height: 40%;
  border: 1px solid black;
  position: fixed;
  bottom: 8%; /* Ajuste conforme necessário */
  left: 82%; /* Ajuste conforme necessário */
  background-color: #cccccc5b;
  border-radius: 20px;
  padding: 30px 20px;
  overflow-y: auto;
  opacity: 1;
  filter: blur(0);
  transition: all 2s;



}



  
}



section#area-conteudo-principal {

	background: orange;
  
}

.alinhar-direita{

	margin-left: auto; 
}

input#pesquisa-jogos {

	margin-top: 80px;
	border-radius: 20px;

}

h2.neymar{

	margin-top: 20px;
	color: black;
}


#segunda_sessao {


	margin-top: 120px;
}

h4.ajuste{

	margin-top: 50px;
	color: blue;

}

.custom {


	background-image: url('../assets/img/lupa.png');
	background-repeat: no-repeat;
	background-size: 60px;
	background-position: -12px;


}

.linear {

    border: 1px solid;
    background: linear-gradient(135deg, #3498db, #e74c3c);
    padding-bottom: 100px;


}

.hidden{

  opacity: 0;
  filter: blur(15px);
  transition: all 2s;
  transform: translateX(-100%);

}


.show{

  opacity: 1;
  filter: blur(0);
  transition: all 2s;
  transform: translateX(0);

}

.hidden-chat{

  opacity: 0;
  filter: blur(0);
  transition: all 2s;
  display: none;
  



}


#foto {

  width: 350px;
  height: 150px;
  margin-bottom: 30px;
  margin-top: 20px;

}

.font{

  font-family: Georgia, 'Times New Roman', Times, serif;

}

.font1{

  font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;

}
/*
.chat{
  
  
  width: 15%;
  height: 40%;
  border: 1px solid black;
  position: fixed;
  bottom: 15%;
  left: 82%;
  background-color: #cccccc5b;
  border-radius: 20px;
  padding: 30px 20px;
  overflow-y: auto;
}
*/

.chat-adm-msg{

  color: black;


}

.chat-adm-msg-auto{

  margin-top: 10px;
  background: #010107;
  color: white;
  border-radius: 5px;
  padding: 15px;

}

.chat-adm-msg-response{

  margin-top: 80px;
  background: #010607;
  color: white;
  border-radius: 5px;
  padding: 5px;
  float: left;
  
}

.chat-user{


  font-size: 25px;
  margin-top: 10px;
  margin-bottom: 5px;
  background: #3957db;
  color: white;
  border-radius: 5px;
  padding: 5px;
  float: right;



}

.chat-input{

  margin-top: 80px;

}




.chat-img{

  width: 5%;
  font-size: 50px;
  transform: scaleX(-1);
  position: fixed;
  bottom: 0; /* Ajuste conforme necessário */
  left: 87%; /* Ajuste conforme necessário */
  height: 8vh; /* Ajuste conforme necessário */
  cursor: pointer;

}

.chat-close {

  float: right;
  margin-top: -10px;
}

</style>