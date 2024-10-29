<template>
  <div class="series">
    <h2>Cadastro de Séries</h2>

    <!-- Inputs para os atributos da série -->
    <div class="form-group">
      <label for="nome">Nome:</label>
      <input v-model="novaSerie.nome" type="text" id="nome" placeholder="Digite o nome da série" />
    </div>

    <div class="form-group">
      <label for="genero">Gênero:</label>
      <input v-model="novaSerie.genero" type="text" id="genero" placeholder="Digite o gênero" />
    </div>

    <div class="form-group">
      <label for="ano">Ano de Lançamento:</label>
      <input v-model="novaSerie.ano" type="number" id="ano" placeholder="Digite o ano" />
    </div>

    <button class="add-button" @click="adicionarSerie">Adicionar Série</button>

    <!-- Lista de séries cadastradas -->
    <div v-if="series.length > 0" class="series-list">
      <h3>Lista de Séries</h3>
      <ul>
        <li v-for="(serie, index) in series" :key="index" class="series-item">
          <span class="series-details">{{ serie.nome }} - {{ serie.genero }} ({{ serie.ano }})</span>
          <button class="delete-button" @click="removerSerie(index)">Remover</button>
        </li>
      </ul>
    </div>
    <p v-else class="empty-message">Não há séries cadastradas.</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      novaSerie: {
        nome: "",
        genero: "",
        ano: ""
      },
      series: []
    };
  },
  methods: {
    adicionarSerie() {
      if (!this.novaSerie.nome || !this.novaSerie.genero || !this.novaSerie.ano) {
        alert("Por favor, preencha todos os campos.");
        return;
      }
      if (isNaN(this.novaSerie.ano) || this.novaSerie.ano <= 0) {
        alert("O ano de lançamento deve ser um número válido.");
        return;
      }

      this.series.push({ ...this.novaSerie });
      this.novaSerie = { nome: "", genero: "", ano: "" };
    },
    removerSerie(index) {
      this.series.splice(index, 1);
    }
  }
};
</script>

<style scoped>
.series {
  max-width: 500px;
  margin: 0 auto;
  padding: 20px;
  background-color: #f8f9fa;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  font-family: Arial, sans-serif;
}

h2 {
  color: #343a40;
  text-align: center;
  margin-bottom: 20px;
}

.form-group {
  margin-bottom: 15px;
}

label {
  display: block;
  font-weight: bold;
  color: #495057;
  margin-bottom: 5px;
}

input {
  width: 100%;
  padding: 10px;
  font-size: 1rem;
  border: 1px solid #ced4da;
  border-radius: 4px;
  box-sizing: border-box;
}

input:focus {
  border-color: #80bdff;
  outline: none;
}

.add-button {
  width: 100%;
  padding: 10px;
  margin-top: 10px;
  background-color: #28a745;
  color: white;
  font-size: 1rem;
  font-weight: bold;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.add-button:hover {
  background-color: #218838;
}

.series-list {
  margin-top: 20px;
}

ul {
  list-style: none;
  padding: 0;
}

.series-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #ffffff;
  border: 1px solid #ced4da;
  border-radius: 4px;
  padding: 10px;
  margin-top: 10px;
}

.series-details {
  color: #495057;
}

.delete-button {
  padding: 5px 10px;
  background-color: #dc3545;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.delete-button:hover {
  background-color: #c82333;
}

.empty-message {
  color: #6c757d;
  text-align: center;
  margin-top: 20px;
  font-style: italic;
}
</style>
