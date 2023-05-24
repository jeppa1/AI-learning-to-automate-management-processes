# AI-learning-to-automate-management-processes
It absorbs data into Python and builds a basic machine learning model that can help automate management processes by taking data from an Excel spreadsheet and using the Pandas library to select input and output features.


# Importar bibliotecas
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestClassifier
from flask import Flask, jsonify, request

# Carregar dados de uma planilha Excel
df = pd.read_excel('dados_erp.xlsx')

# Selecionar os recursos de entrada e saída
X = df.drop('cliente', axis=1)
y = df['cliente']

# Dividir dados em conjuntos de treinamento e teste
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Treinar modelo de aprendizado de máquina
rf = RandomForestClassifier()
rf.fit(X_train, y_train)

# Iniciar o servidor Flask
app = Flask(__name__)

# Definir rota para previsão de cliente
@app.route('/predict', methods=['POST'])
def predict():
    data = request.json
    input_data = pd.DataFrame.from_dict(data)
    prediction = rf.predict(input_data)
    return jsonify({'prediction': prediction.tolist()})

# Executar o servidor Flask
if __name__ == '__main__':
    app.run(debug=True)

# Importar biblioteca csv
import csv

# Abrir arquivo CSV
with open('dados.csv', newline='') as arquivo_csv:

    # Criar leitor CSV
    leitor_csv = csv.DictReader(arquivo_csv)

    # Criar lista vazia para armazenar dicionários
    lista_dicionarios = []

    # Iterar sobre as linhas do arquivo CSV
    for linha in leitor_csv:

        # Adicionar dicionário à lista
        lista_dicionarios.append(linha)

# Exibir lista de dicionários
print(lista_dicionarios)

# Importar biblioteca csv
import csv

# Abrir arquivo CSV
with open('dados.csv', newline='') as arquivo_csv:

    # Criar leitor CSV
    leitor_csv = csv.DictReader(arquivo_csv)

    # Criar lista vazia para armazenar dicionários
    lista_dicionarios = []

    # Iterar sobre as linhas do arquivo CSV
    for linha in leitor_csv:

        # Adicionar dicionário à lista
        lista_dicionarios.append(linha)

# Exibir lista de dicionários
print(lista_dicionarios)

# Importar biblioteca Flask
from flask import Flask

# Criar instância do Flask
app = Flask(__name__)

# Definir rota raiz
@app.route('/')
def index():
    return 'Olá, mundo! Este é o meu servidor web!'

# Executar aplicação
if __name__ == '__main__':
    app.run()
import React from 'react';

function App() {
  return (
    <div>
      <h1>Minha Aplicação React</h1>
      <p>Bem-vindo ao meu aplicativo!</p>
    </div>
  );
}

export default App;
import React from 'react';
import ReactDOM from 'react-dom';
import App from './App';

ReactDOM.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
  document.getElementById('root')
);

<template>
  <div>
    <h1>Minha Aplicação Vue</h1>
    <p>Bem-vindo ao meu aplicativo!</p>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

import Vue from 'vue'
import App from './App.vue'

Vue.config.productionTip = false

new Vue({
  render: h => h(App),
}).$mount('#app')
