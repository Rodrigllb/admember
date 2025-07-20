<template>
  <div id="main-container">
    <div class="body-page">

      <main>
        <section class="marca-afins">
          <img src="../assets/logo/logo-admembers.png" alt="logo admembers">
          <small>Formulário destinado ao cadastro e à gestão interna dos membros da Igreja Assembleia de Deus – Templo Central do Gravier.</small>
        </section>
        <section class="formulario-preenchimento">
          
          <form id="formulario"> 

            <div class="miniDash">
            <h3>MEMBROS</h3>
            <input type="text" id="dashboard-mini" readonly>
            </div>

            <input type="text" placeholder="Digite o nome completo" id="nome-member" required>
            <input type="text" name="data" id="aniversario-member" placeholder="Digite a data de aniversário" required>
            <select name="lista-cargo" id="cargo-atual">
              <option value="Selecione o cargo atual">Selecione o cargo atual</option>
              <option value="Ovelha">Ovelha</option>
              <option value="Pastor">Pastor</option>
              <option value="Diácono">Diácono</option>
              <option value="Presbítero">Presbítero</option>
              <option value="Auxiliar">Auxiliar</option>
              <option value="Tia da salinha">Tia da salinha</option>
              <option value="Presidente dos jovens">Presidente dos Jovens</option>
              <option value="Vice presidente dos jovens">Vice presidente dos Jovens</option>
              <option value="Regente do circulo de oração">Regente do circulo de oração</option>
              <option value="Regente de Senhoras">Regente de senhoras</option>
              <option value="Regente de Jovens">Regente de jovens</option>
              <option value="Regente de Crianças">Regente de crianças</option>
            </select>
            <input type="submit" value="Cadastrar informações" id="enviar-dados">
            <small>Deseja nos conhecer? Visite nosso site clicando <a href="https://adtcgravier.netlify.app/" target="_blank">aqui.</a></small>
          </form>
        </section>
        <section class="rodape-formulario">
          <small>Developed by Rodrigo Liberato V1.2</small>
          
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
      const response = await fetch('https://script.google.com/macros/s/AKfycbygBdycBdhI4oCBKfsXrTxwgxIEfglWKbmr1LqcdiP3bAVuDnp2nCImeTUOUG6WGeE/exec', {
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

  async function buscardados() {
    try { //Tentativa de buscar dados da celula da planilha.
      const response = await fetch("https://script.google.com/macros/s/AKfycbygBdycBdhI4oCBKfsXrTxwgxIEfglWKbmr1LqcdiP3bAVuDnp2nCImeTUOUG6WGeE/exec");
      const data = await response.json();
      document.getElementById('dashboard-mini').value = data.valor;
    }
    catch (erro){
      console.error("Erro ao buscar dados..");
    }
  }

  buscardados();
  setInterval(buscardados, 100);

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
  width: 350px;
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
  border-radius: 10px;
  background-color: #eee;
}
.formulario-preenchimento small {
  font-size: 9pt;
  color: #686868ee;
}
#enviar-dados {
  background-color: #4a90e2;
  color: #fff;;
}

.miniDash { /*Estilização do mini dashboard da quantidade de membros*/
  display: flex;
  flex-direction: row;
  width: 100%;
  height: 62px;
  align-items: center;
  justify-content: center;
  border-radius: 15px;
  border: 1px solid #4a90e2;
}

#dashboard-mini { /*Saída de dados da quantidade de membros cadastrados*/
  display: flex;
  width: 53px;
  font-size: 15pt;
  text-align: center;
  font-weight: 700;
  border-radius: 50%;
  outline: none;
  color: #4a90e2;
  background-color: transparent;
}

.rodape-formulario {
   font-size: 9pt;
}


</style>