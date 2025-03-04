# Trabalhando com Machine Learning na Prática no Azure ML

Passo a passo do projeto **Trabalhando com Machine Learning na Prática no Azure ML** da DIO.

## Links importantes

- [Explore Azure AI Services](https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/02-content-safety.html)
- [Explore Automated Machine Learning in Azure Machine Learning](https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/01-machine-learning.html)
- **Fonte dos dados**:  
  - [Página de acesso](https://aka.ms/bike-rentals)  
  - [Link direto para o dataset](https://raw.githubusercontent.com/MicrosoftLearning/mslearn-ai-fundamentals/main/data/ml/daily-bike-share.csv)

---

## Passo 1: Criando recurso do Azure Machine Learning

Primeiro, criei um recurso de **Machine Learning**. Para isso:
1. Cliquei em **"Criar recurso"**.
2. Pesquisei por **Azure Machine Learning** no marketplace.
3. Após identificar o recurso, cliquei em **Criar**.

![Criação do Recurso](./imgs/img1.gif)

---

## Passo 2: Configurando o recurso do Azure Machine Learning

1. Na aba **Noções básicas**, informei:
   - **Assinatura** para cobrança.
   - **Grupo de recursos** que englobará o recurso criado.

2. Em **Detalhes da área de trabalho**, preenchi as informações do workspace. Como foi um **lab**, utilizei as configurações mínimas.
3. Cliquei em **Consultar + Criar**.
4. Após a validação, cliquei em **Criar**.

![Configuração do Recurso](./imgs/img2.png)

Após a criação:
- Cliquei em **"Ir para o recurso"** para acessar a página correspondente.

![Ir para o recurso](./imgs/img3.png)

- Nessa página, utilizei o botão **"Iniciar o estúdio"**, que me redirecionou para a página do estúdio do **Azure Machine Learning**.

![Iniciar o estúdio](./imgs/img4.png)

---

## Passo 3: Criando o modelo

1. No **Estúdio do Azure ML**, acessei **ML automatizado**.
2. Cliquei em **"Novo trabalho de ML automatizado"**.

![Novo trabalho de ML](./imgs/img5.gif)

### **Configuração do Trabalho**
1. Preenchi os campos:
   - **Nome do trabalho**.
   - **Novo nome do experimento**.
   - **Descrição**.
2. Cliquei em **Avançar**.

### **Selecionando os dados**
1. Escolhi o tipo de tarefa como **Regressão**.
2. Em **Selecionar dados**, cliquei em **Criar**.
3. No modal:
   - Preenchi os campos **Nome** e **Descrição**.
   - Escolhi **Tipo: Tabular**.
   - Cliquei em **Avançar**.
4. No passo **Fonte de dados**, selecionei **De arquivos da Web** e cliquei em avançar.
5. No campo **URL da Web**, informei:  
   - [https://aka.ms/bike-rentals](https://aka.ms/bike-rentals).
6. Ajustei as configurações do conjunto de dados, verifiquei os tipos de dados e finalizei.

![Selecionar dados](./imgs/img6.gif)

### **Configurações da Tarefa**
1. Escolhi o conjunto de dados importado.
2. Defini a **coluna de destino** como **rentals**.
3. Em **Limite**, preenchi os valores adequados e ativei **Habilitar encerramento antecipado**.

![Configurações](./imgs/img7.png)

4. Em **Validar e testar**, selecionei **Divisão de validação de treinamento**.
5. No passo **Computação**, mantive os valores padrão.

![Computação](./imgs/img8.png)

6. Finalizei clicando em **"Enviar trabalho de treinamento"**.

### **Registrando o Modelo**
1. Após a conclusão do treinamento, acessei a página do trabalho.
2. Cliquei em **"Modelo de registro"**.
3. Preenchi o nome e a versão do modelo e cliquei em **Criar**.

![Registro do Modelo](./imgs/img12.gif)

- O modelo agora está acessível na aba **"Modelos"**.

![Modelos](./imgs/img9.png)

---

## Passo 4: Métricas do Modelo

1. Para acessar as métricas do modelo treinado:
   - Na página do modelo, cliquei em **"Criado por trabalho"**.
   - Também é possível acessar via **"Tarefas (Jobs)"** no menu lateral.
2. Na página da tarefa, acessei a aba **Métricas**.

![Métricas do Modelo](./imgs/img10.gif)

---

## Passo 5: Teste do Modelo

1. Na página do modelo, acessei a aba **"Pontos de extremidade"**.
2. Cliquei em **"Implantar"**, porém, o botão não funcionou.
3. Como alternativa:
   - Acessei **"Pontos de extremidade"** no menu lateral.
   - Cliquei em **Criar**.
   - Marquei o modelo e deixei os valores padrão, exceto:
     - **Contagem de instâncias**: **1**.
   - Cliquei em **Implantar**.

![Criando o Ponto de Extremidade](./imgs/img13.gif)

4. Após a implantação (média de **9 a 10 minutos**), acessei a aba **"Testar"** do ponto de extremidade.
5. Testei com o JSON abaixo:

```json
{
  "input_data": {
    "data": [
       {
         "day": 1,
         "mnth": 1,   
         "year": 2022,
         "season": 2,
         "holiday": 0,
         "weekday": 1,
         "workingday": 1,
         "weathersit": 2, 
         "temp": 0.3, 
         "atemp": 0.3,
         "hum": 0.3,
         "windspeed": 0.3 
       }
     ]
  }
}
