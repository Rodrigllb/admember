<template>
  <div id="main-container">
    <div class="body-page">

      <main>
        <section class="marca-afins">
          <img src="../assets/logo/logo-admembers.png" alt="logo admembers">
          <small>Plataforma destinada ao cadastro e à gestão interna dos membros da Igreja Assembleia de Deus – Templo Central do Gravier.</small>
        </section>
        <section class="formulario-preenchimento">
          <form id="formulario">
            <input type="text" placeholder="Digite o nome completo" id="nome-member" required>
            <input type="text" name="data" id="aniversario-member" placeholder="Digite a data de aniversário" required>
            <select name="lista-cargo" id="cargo-atual">
              <option value="Selecione o cargo atual">Selecione o cargo atual</option>
              <option value="Pastor">Pastor</option>
              <option value="Diácono">Diácono</option>
              <option value="Presbítero">Presbítero</option>
              <option value="Auxiliar">Auxiliar</option>
              <option value="Porteiro">Porteiro</option>
              <option value="Evangelista">Evangelista</option>
              <option value="Ovelha">Ovelha</option>
              <option value="Regente de Jovens">Regente de jovens</option>
              <option value="Regente de Crianças">Regente de crianças</option>
            </select>
            <input type="submit" value="Cadastrar informações" id="enviar-dados">
            <small>Deseja nos conhecer? Visite nosso site clicando <a href="https://adtcgravier.netlify.app/" target="_blank">aqui.</a></small>
          </form>
        </section>
        <section class="rodape-formulario">
          <small>Developed by Rodrigo Liberato V1.0</small>
          
        </section>
      </main>

    </div>
  </div>
</template>

<script>

export default {
  name: 'homePage',
}


document.addEventListener('DOMContentLoaded', ()=> {

  const inserirInformacoesForm = document.getElementById('formulario');
  inserirInformacoesForm.addEventListener('submit', async (event) => {
    event.preventDefault();

    const nome = document.getElementById('nome-member').value;
    const aniversario = document.getElementById('aniversario-member').value;
    const cargo = document.getElementById('cargo-atual').value;
    
    try {
      const response = await fetch('https://script.google.com/macros/s/AKfycbw-uD0HFhqRnKcXj-4wBvuFyyDgLulJINO6Nh-wuczQGqrwpkahFxcvd930azENmmU/exec', {
        method: 'POST',
        mode: 'no-cors',
        headers: {
          'Content-type': 'application/json',
        },
        body: JSON.stringify({nome, aniversario, cargo})
      });

      //Verificar se a requisição foi bem-sucedida
      if (response.ok) {
        alert('Cadastro realizado com sucesso, no modo no-cors!');
      } else {
        alert('Cadastro realizado com sucesso!')
      }
    
      inserirInformacoesForm.reset();
      

    } catch (error) { //Caso o envio dos dados não seja bem sucedida.
      console.error('Erro ao enviar dados do membro.');
      alert('Ocorreu um erro, favor contatar ao desenvolvedor.')
    }

 
  
  });

});
</script>

<style scoped>

* { /*Configurações globais*/
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

#main-container { /*Container principal*/
  display: flex;
  width: 100%;
  height: auto;
  align-items: center;
  justify-content: center;
  margin: 0 auto;
}

.body-page { /*Corpo da pagina*/
  display: flex;
  align-items: center;
  justify-content: center;
  width: 400px;
  height: auto;
  padding: 12px;
  margin: 0 auto;
  border-radius: 25px;
}

main { /*Elemento semântico da página*/
  display: flex;
  margin: 0 auto;
  flex-direction: column;
  width: 100%;
  height: 680px;
}

.marca-afins { /*Containers da logo*/
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 300px;
  height: 200px;
  margin: 0 auto;
  
}
.marca-afins small {
  text-align: center;
}
.marca-afins img { /*Local da logo */
  width: 252px;
  height: auto;
}

.formulario-preenchimento { /*Formulário para preenchimento dos dados dos membros da igreja para levantamento interno*/
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 400px;
}
.formulario-preenchimento form { /*Estilização do formulário e seus elementos */
  display: flex;
  flex-direction: column;
  width: 100%;
  height: auto;
}
.formulario-preenchimento input { /*Estilização das entradas de dados*/
  
  border: 1px solid #000;
  padding: 13px;
  margin: 15px 0px 15px 0px;
  border: none;
  border-radius: 25px;
  background-color: #eeeeee;
}
.formulario-preenchimento select {
  border: 1px solid #000;
  padding: 13px;
  margin: 15px 0px 15px 0px;
  border: none;
  border-radius: 25px;
  background-color: #eeeeee;
}
.formulario-preenchimento small {
  font-size: 9pt;
  color: #686868ee;
}
#enviar-dados {
  background-color: #4a90e2;
  color: #fff;;
}


.rodape-formulario {
   font-size: 9pt;
}


</style>