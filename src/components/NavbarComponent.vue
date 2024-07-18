<template>

  <div>
      
    <!-- Início Navegação -->
    <nav class="navbar navbar-expand-lg navbar-light bg-primary">

      <!-- Início Logo -->
      <a class="navbar-brand" href="#">
        <img src="../assets/img/logo1.png" width="192" class="img-fluid" alt="Logo">
      </a> <!-- Fim Logo -->

      


      <!-- Início Menu Hamburguer -->
      <div class="menuHamburger">
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navegacao-principal" aria-controls="navegacao-principal" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button><!-- Fim Menu Hamburguer -->
      </div>

      <!-- Início Navegação Listas -->
      <div class="collapse navbar-collapse" id="navegacao-principal">




        <!-- Início Ul -->
        <ul class="navbar-nav alinhar-direita">

          <li class="nav-item">
            <a class="btn text-dark nav-link mr-2 celular activate under" href="#">Home</a>
          </li>

          <!-- Botão Entrar -->
          <li v-if="showEntrar" class="nav-item">
            <a @click="logar" id="entrar" class="btn text-dark nav-link mr-2 celular under" href="#">Entrar</a>
          </li><!-- Botão Entrar -->

          <!-- Botão Cadastrar -->
          <li v-if="showCadastrar" class="nav-item">
            <a @click="cadastrar" class="btn text-dark nav-link celular under" href="#">Cadastre-Se</a>
          </li><!-- Botão Cadastrar -->

          <!---Usuario--->
          <li v-if="showUser" class="nav-item align">
            <a @click="abrirBoxUser" class="nav-link" href="#">
              <img class="icon" src="../assets/img/user.png" alt="">
            </a>
          </li>

          <!---Logar--->
          <li v-if="showUser" class="nav-item adjustLogout">
            <a @click="logout" class="nav-link" href="#">
              Logout
            </a>
          </li>




        

        </ul><!-- Fim Ul -->

      </div><!-- Fim Navegação Listas -->

      <ModalController />

    </nav><!-- Fim Navegação -->

  </div>


  <!-- Modal Aviso -->
  <button
    id="warning"
    type="button"
    class="btn btn-primary btn-lg d-none"
    data-bs-toggle="modal"
    data-bs-target="#modalId"
  >
    Launch
  </button>
  
  <!-- Modal Aviso -->

  <div
    class="modal fade"
    id="modalId"
    tabindex="-1"
    data-bs-backdrop="static"
    data-bs-keyboard="false"
    
    role="dialog"
    aria-labelledby="modalTitleId"
    aria-hidden="true"
  >
    <div
      class="modal-dialog modal-dialog-scrollable modal-dialog-centered modal-sm"
      role="document"
    >
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="modalTitleId">
            Aviso Cadastre-Se
          </h5>
          <button
            type="button"
            class="btn-close"
            data-bs-dismiss="modal"
            aria-label="Close"
          ></button>
        </div>
        <div class="modal-body">
          Ao clicar no botão "Concordar" na plataforma da PLAZE, você está oficialmente declarando e confirmando ser maior de idade. Essa ação reflete seu pleno entendimento e aceitação das políticas, termos e condições estabelecidos pela casa de apostas fictícia PLAZE. É crucial revisar minuciosamente todas as informações disponibilizadas antes de concordar, uma vez que essa concordância implica seu consentimento e conformidade com as diretrizes estabelecidas pela PLAZE. Caso haja dúvidas ou inseguranças, recomendamos buscar esclarecimentos adicionais junto à equipe de suporte. Ressaltamos a importância de agir de acordo com as leis e regulamentações locais relacionadas à idade e ao consentimento em atividades de apostas. <br><br>

        <input @click="accept" value="0" id="aceitar_termos" type="radio" name="">
        <label>Concordar</label><br>
        <div class="bg-danger text-light rounded-4 text-center mt-2">{{recusado}}</div>
        
        </div>
        <div class="modal-footer">
          <button
            type="button"
            class="btn btn-secondary"
            data-bs-dismiss="modal"
          >
            Fechar
          </button>
          <button @click="cadastro" type="button" class="btn btn-primary">Ir Para O  Cadastro</button>
        </div>
      </div>
    </div>
  </div>

  

  <!--  Modal Register  -->
  <button
    id="register"
    type="button"
    class="btn btn-primary btn-lg d-none"
    data-bs-toggle="modal"
    data-bs-target="#modalId2"
  >
    Launch
  </button>
  
  <!-- Modal Register-->
  <div
    class="modal fade"
    id="modalId2"
    tabindex="-1"
    role="dialog"
    aria-labelledby="modalTitleId"
    aria-hidden="true"
  >
    <div class="modal-dialog" role="document">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="modalTitleId">
            Cadastrar
          </h5>
          <button
            type="button"
            class="btn-close"
            data-bs-dismiss="modal"
            aria-label="Close"
          ></button>
        </div>
        <div class="modal-body">
          <div class="container-fluid">

        <label class="text-uppercase text-primary">Digite Seu Email<span id="alerta3"></span></label>
        <input @keyup="validarEmail" id="registrar_email" class="form-control" type="email" name="" placeholder="Preencha o Campo Com o E-mail">
        <div class="mt-1 bg-danger rounded-4 text-light text-center" v-if="warningEmail != null">
          {{warningEmail}}
        </div>
         <label class="text-uppercase text-info mt-4">Digite Sua Data de Nascimento<span id="alerta1"></span></label>
          <input @click="notificarData" id="registrar_data" class="form-control" type="date" name="">
        <div class="mt-1 bg-danger rounded-4 text-light text-center" v-if="warningAGE != null">
          {{warningAGE}}
        </div>

        <label class="text-uppercase text-secondary mt-4">Digite Sua Senha<span id="alerta2"></span></label>
        <input @keyup="validaSenha" id="registrar_senha" class="form-control " type="password" name="" placeholder="Preencha o Campo Com a SENHA">
        <div class="mt-1 bg-danger rounded-4 text-light text-center" v-if="warningSENHA != null">
          {{warningSENHA}}
        </div>

        <label class="text-uppercase text-warning mt-4">Confirme Sua Senha<span id="alerta_confirmarSenha"></span></label>
        <input @keyup="validaPassword" id="confirmar_senha" class="form-control mb-4 " type="password" name="" placeholder="Preencha o Campo Com a SENHA">
        <div class="mt-1 bg-danger rounded-4 text-light text-center" v-if="warningPassword != null">
          {{warningPassword}}
        </div>
        <label class="text-uppercase text-dark mt-4">Codigo Afiliado (opcional)<span id="alerta_confirmarSenha"></span></label>
        <input id="afiliado" class="form-control mb-4 " type="number" name="" placeholder="Preencha o Campo Com o Codigo Afiliado">

        <div class="mt-1 bg-danger rounded-4 text-light text-center" v-if="warningHTTP != null">
          {{warningHTTP}}
        </div>

        <div v-if="loading" class="ploading">
          <img class="loading" src="../assets/gif/loading.gif" alt="">
        </div>

      
        <div v-if="psuccess" class="psuccess">
          <img class="success" src="../assets/gif/success.gif" alt="">
        </div>
        


        
        
      </div>
      <div class="modal-footer">
        <button id="close"  type="button" class="btn btn-secondary" data-bs-dismiss="modal">Fechar</button>
        <button @click="confirmarCadastro" id="login" type="button" class="btn btn-primary">Cadastrar-Se</button>



          </div>
        </div>
      </div>
    </div>
  </div>


    <!--  Modal Login  -->
  <button
    id="loginn"
    type="button"
    class="btn btn-primary btn-lg d-none"
    data-bs-toggle="modal"
    data-bs-target="#modalId3"
  >
    Launch
  </button>
  
  <!-- Modal Login-->
  <div
    class="modal fade"
    id="modalId3"
    tabindex="-1"
    role="dialog"
    aria-labelledby="modalTitleId"
    aria-hidden="true"
  >
    <div class="modal-dialog" role="document">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="modalTitleId">
            Login
          </h5>
          <button
            type="button"
            class="btn-close"
            data-bs-dismiss="modal"
            aria-label="Close"
          ></button>
        </div>
        <div class="modal-body">
          <div class="container-fluid">

        <label class="text-uppercase text-primary">Digite Seu Email<span id="alerta1"></span></label>
        <input @keypress="validarEmailLogin" id="email" class="form-control" type="email" name="" placeholder="Preencha o Campo Com o Email">
        <div class="mt-1 bg-danger rounded-4 text-light text-center" v-if="warningEmail != null">
          {{warningEmail}}
        </div>
        <label class="text-uppercase text-secondary mt-4">Digite Sua Senha<span id="alerta2"></span></label>
        <input  id="senha" class="form-control " type="password" name="" placeholder="Preencha o Campo Com a SENHA">
        <div class="mt-1 bg-danger rounded-4 text-light text-center" v-if="warningEmail != null">
          {{warningPassword}}
        </div>

         <div class="mt-1 bg-danger rounded-4 text-light text-center" v-if="warningHTTP != null">
          {{warningHTTP}}
        </div>

        <div v-if="loading" class="ploading">
          <img class="loading" src="../assets/gif/loading.gif" alt="">
        </div>

        <div v-if="psuccess" class="psuccess">
          <img class="success" src="../assets/gif/success.gif" alt="">
        </div>
        


        <br>


        
      </div>
      <div class="modal-footer">
        <button id="closelogin"  type="button" class="btn btn-secondary" data-bs-dismiss="modal">Fechar</button>
        <button  @click="autenticacao" id="login" type="button" class="btn btn-primary">Login</button>



          </div>
        </div>
      </div>
    </div>
  </div>

     <!--  Modal User  -->
  <button
    id="datauser"
    type="button"
    class="btn btn-primary btn-lg d-none"
    data-bs-toggle="modal"
    data-bs-target="#modalId4"
  >
    Launch
  </button>
  
  <!-- Modal User-->
  <div
    class="modal fade"
    id="modalId4"
    tabindex="-1"
    role="dialog"
    aria-labelledby="modalTitleId"
    aria-hidden="true"
  >
    <div class="modal-dialog" role="document">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="modalTitleId">
            Dados do Usuario
          </h5>
          <button
            type="button"
            class="btn-close"
            data-bs-dismiss="modal"
            aria-label="Close"
          ></button>
        </div>
        <div class="modal-body">
          <div class="container-fluid">

        <label class="text-uppercase text-primary">Email</label>
        <input id="email" class="form-control" type="email" name="" :value="email" disabled>


        <label class="text-uppercase text-secondary mt-4">Senha</label>
        <input  id="senha" class="form-control " type="password" name="" value="*********" disabled>

        <label class="text-uppercase text-secondary mt-4">Data</label>
        <input  id="senha" class="form-control " type="text" name="" :value="data" disabled>

        <label class="text-uppercase text-secondary mt-4">Codigo Afiliado</label>
        <input  id="senha" class="form-control " type="text" name="" :value="cdg" disabled>


        


        <br>


        
      </div>
      <div class="modal-footer">
        <button id="closelogin"  type="button" class="btn btn-secondary" data-bs-dismiss="modal">Fechar</button>


          </div>
        </div>
      </div>
    </div>
  </div>
  
  

  


  
  
</template>


<script>

import axios from "axios"

export default {

  data() {

    return {

      id: null,
      user: null,
      email: null,
      data: null,
      cdg: null,
      showEntrar: true,
      showCadastrar: true,
      showUser: false,
      aceito: false,
      recusado: '',
      warningEmail: null,
      warningSENHA: null,
      warningPassword: null,
      warningAGE: null,
      warningHTTP: null,
      blockEmail: true,
      blockSENHA: true,
      blockAGE: true,
      loading: false,
      psuccess: false

      


    }

  },

  mounted() {

    if(this.cdg == null) {

      this.cdg = 'Nenhum Codigo'

    }


  },


  methods: {

    logar: function () {

      document.getElementById('loginn').click()

    },


    cadastrar: function() {

      document.getElementById('warning').click()
      

    },

    accept: function() {

      this.aceito = true

    },

    cadastro: function() {

      if(this.aceito) {

        document.getElementById('register').click()
        this.recusado = ''

      }else {

        this.recusado = 'Ops Confirme Por Favor'


      }

    },

    validarEmailLogin: function() {


    },

    validarEmail: function() {
      

      var email = document.getElementById('registrar_email').value



        if(email !=  '') {

          this.blockEmail = false
          this.warningEmail = null

        }

        

    },

    validaSenha: function() {

      var senha = document.getElementById('registrar_senha').value


      if(senha != '') {

        this.warningSENHA = null

      }

    },

    validaPassword: function() {

      var senha = document.getElementById('registrar_senha').value
      var cfSenha = document.getElementById('confirmar_senha').value


      if(senha != cfSenha) {

        this.warningPassword = 'Senha Diferente'

      }else {

        this.blockSENHA = false
        this.warningPassword = null

      }


    },

    notificarData: function() {

      this.warningAGE = null

    },

  confirmarCadastro: function() {
  var email = document.getElementById('registrar_email').value
  var senha = document.getElementById('registrar_senha').value
  var cfSenha = document.getElementById('confirmar_senha').value


  if(email == '' || email == undefined) {

    this.warningEmail = 'EMAIL INVALIDO'

  }

  if(senha == '' || senha == undefined) {

    this.blockSENHA = false
    this.warningSENHA = 'SENHA INVALIDA'

  }

  if(cfSenha == '' || cfSenha == undefined) {

    this.warningPassword = 'SENHA INVALIDA'

  }



  var data = document.getElementById('registrar_data').value
  var date = data.split('-')
  var newData = date[2] + '/' + date[1] + '/' + date[0]

  const parts = newData.split('/');
  const day = parseInt(parts[0], 10);
  const month = parseInt(parts[1], 10) - 1; 
  const year = parseInt(parts[2], 10);

 
  const birthDate = new Date(year, month, day);

  const today = new Date();


  let age = today.getFullYear() - birthDate.getFullYear();
  const monthDifference = today.getMonth() - birthDate.getMonth();
  const dayDifference = today.getDate() - birthDate.getDate();

 
  if (monthDifference < 0 || (monthDifference === 0 && dayDifference < 0)) {
    age--;
  }



  if(age >= 18) {

    this.blockAGE = false
    this.warningAGE = null

  }else {

    this.warningAGE = 'Menor de 18 Anos'

  }


  if(this.blockEmail || this.blockSENHA || this.blockAGE) {

      //
      console.log(this.blockEmail)
      console.log(this.blockSENHA)
      console.log(this.blockAGE)


  }else {

    //Cadastrar
    this.warningEmail = null
    this.warningSENHA = null
    this.warningPassword = null
    this.warningAGE = null
    this.loading = true

    var emailField = document.getElementById("registrar_email").value
    var passwordField = document.getElementById("registrar_senha").value
    var dataField = document.getElementById("registrar_data").value
    var cdgField = document.getElementById("afiliado").value

    axios.post('https://projeto-api-plaze.vercel.app/register', {

      email: emailField,
      password: passwordField,
      data: dataField,
      cdg: cdgField

    }).then( () => {

      
      this.loading = false
      this.psuccess = true
      this.warningHTTP = null



      setTimeout(() => {

        this.psuccess = false
        document.getElementById('close').click()
        document.getElementById('entrar').click()
        
      }, 2020);


    


    }).catch(err => {

      this.loading = false

      this.warningHTTP = err.response.data.err


    })

    

  }





},

  autenticacao: function() {

    var emailLogin = document.getElementById('email').value 
    var senhaLogin = document.getElementById('senha').value 

    if(emailLogin == undefined || emailLogin == '' || emailLogin == ' ') {

      this.warningEmail = 'O Email E Invalido Verifique Novamente'

    }

    if(senhaLogin == undefined || senhaLogin == '' || senhaLogin == ' ') {

      this.warningPassword = 'A Senha E Invalida Verifique Novamente'

    }else {

      this.loading = true
      this.warningEmail = null
      this.warningPassword = null

      axios.post("https://projeto-api-plaze.vercel.app/login", {
        email: emailLogin,
        password: senhaLogin
      }).then( res => {

      this.loading = false
      this.psuccess = true
      this.warningHTTP = null
      this.showEntrar = false,
      this.showCadastrar = false,
      this.showUser = true,

      localStorage.setItem("token", res.data.token)

      axios.post("https://projeto-api-plaze.vercel.app/verify", {
        token: res.data.token
      }).then(res => {

        var oldDate = res.data.data[0].data.split('-')
        var fixDate = oldDate[2] + '/' + oldDate[1] + '/' + oldDate[0]


        this.id = res.data.data[0].id
        this.user = res.data.data[0].user
        this.email = res.data.data[0].email
        this.data = fixDate
        this.cdg = res.data.data[0].cdgafiliado


      }).catch(err => {

        console.log(err)


      })
    

      setTimeout(() => {

        this.psuccess = false
        document.getElementById('closelogin').click()
        
      }, 2020);

      }).catch(err => {

      this.loading = false
      this.warningHTTP = err.response.data.err

      })


    }


    


  },


  abrirBoxUser: function() {

    document.getElementById('datauser').click()

  },

  logout: function() {

      this.id = null
      this.user = null
      this.email = null
      this.data = null
      this.cdg =  null
      this.showEntrar = true
      this.showCadastrar = true
      this.showUser = false


  }


  }


}
</script>

<style>

@media(max-width: 988px) {

  .align{

    margin-left: 97px;

  }

  .menuHamburger {

    margin-left: 480px;

}

.adjustLogout {

  display: flex;
  justify-content: center;
  position: absolute;
  left: 52%;
  transform: translateX(-50%);
  width: 70px;

}


  
}

@media(max-width: 750px) {


  .menuHamburger {

    margin-left: 380px;

}

  
}

@media(max-width: 650px) {


  .menuHamburger {

    margin-left: 280px;

}

  
}

@media(max-width: 550px) {


  .menuHamburger {

    margin-left: 170px;

}

}

@media(max-width: 450px) {


  .menuHamburger {

    margin-left: 0;

}

}



.alinhar-direita{

	margin-left: auto; 
}

a.btn.under {

    margin-left: 20px;
    padding: 0;

    

}

a.btn.under:hover {

    
   border-bottom: 4px solid rgb(0, 255, 34);
   transition: 0.1s;



}

.ploading{

  display: flex;
  justify-content: center;
  
}

.loading{

  margin-top: 20px;
  width: 5vh;
  margin-bottom: 20px;

  

}

.psuccess{

  display: flex;
  justify-content: center;

  
}

.success{

  margin-top: 20px;
  width: 50vh;

  

}


.icon{

  height: 5vh;
  margin-top: -18px;


}

.align {

  display: flex;
  justify-content: center;
  padding-right: 80px;


}

.adjustLogout {

 position: relative;
 top: -5px;
 right: 60px;
 background: rgba(255, 0, 0, 0.822);
 border-radius: 15px;

}


</style>