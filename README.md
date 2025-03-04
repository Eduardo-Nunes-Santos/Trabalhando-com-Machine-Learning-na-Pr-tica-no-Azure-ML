# Trabalhando com Machine Learning na Prática no Azure ML 🌐

🎯Desafio da DIO  **Trabalhando com Machine Learning na Prática no Azure ML**.🌐

📌## Links importantes 🧑‍💻

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

![Captura de tela 2025-03-01 005019](https://github.com/user-attachments/assets/46a6349b-1270-40cf-b1dd-a27338155845)


---

## Passo 2: Configurando o recurso do Azure Machine Learning

1. Na aba **Noções básicas**, informei:
   - **Assinatura** para cobrança.
   - **Grupo de recursos** que englobará o recurso criado.

2. Em **Detalhes da área de trabalho**, preenchi as informações do workspace. Como foi um **lab**, utilizei as configurações mínimas.
3. Cliquei em **Consultar + Criar**.
4. Após a validação, cliquei em **Criar**.

![Captura de tela 2025-03-01 005309](https://github.com/user-attachments/assets/7fcc1a01-ec42-45a6-9453-b10afb2676ee)



Após a criação:
- Cliquei em **"Ir para o recurso"** para acessar a página correspondente.

![Captura de tela 2025-03-01 013812](https://github.com/user-attachments/assets/0ab38152-0da5-4993-8b62-36a45f63ea9a)

- Nessa página, utilizei o botão **"Iniciar o estúdio"**, que me redirecionou para a página do estúdio do **Azure Machine Learning**.
![Captura de tela 2025-03-01 013812](https://github.com/user-attachments/assets/b4329ba8-4918-4dbe-9201-fbdbcd69be5a)


---

## Passo 3: Criando o modelo

1. No **Estúdio do Azure ML**, acessei **ML automatizado**.
2. Cliquei em **"Novo trabalho de ML automatizado"**.
![Captura de tela 2025-03-01 014134](https://github.com/user-attachments/assets/409042da-78c9-45d8-9cd0-221f972a499a)


### **Configuração do Trabalho**
1. Preenchi as seguintes informações:
- Nome do trabalho
- Nome do experimento
- Descrição
2. Após preencher os campos, avancei para a próxima etapa clicando em Avançar.

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

![Captura de tela 2025-03-01 014905](https://github.com/user-attachments/assets/db708dee-fda0-4806-9b41-a884c97fb912)

### **Configurações da Tarefa**
1. Escolhi o conjunto de dados importado.
2. Defini a **coluna de destino** como **rentals**.
3. Em **Limite**, preenchi os valores adequados e ativei **Habilitar encerramento antecipado**.


4. Em **Validar e testar**, selecionei **Divisão de validação de treinamento**.
5. No passo **Computação**, mantive os valores padrão.


6. Finalizei clicando em **"Enviar trabalho de treinamento"**.

### **Registrando o Modelo**
1. Após a conclusão do treinamento, acessei a página do trabalho.
2. Cliquei em **"Modelo de registro"**.
3. Preenchi o nome e a versão do modelo e cliquei em **Criar**.


- O modelo agora está acessível na aba **"Modelos"**.
![Captura de tela 2025-03-01 022922](https://github.com/user-attachments/assets/f94dd880-735b-4665-9ad8-8712f83589cb)


---

## Passo 4: Métricas do Modelo

1. Para acessar as métricas do modelo treinado:
   - Na página do modelo, cliquei em **"Criado por trabalho"**.
   - Também é possível acessar via **"Tarefas (Jobs)"** no menu lateral.
2. Na página da tarefa, acessei a aba **Métricas**.

![Captura de tela 2025-03-01 023226](https://github.com/user-attachments/assets/4b1d2ed6-5768-4841-9497-826ab1ad3eac)

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
  
     ## Configurações para implantar

     - Máquina virtual : Standard_DS3_v2
     - Contagem de instâncias : 3
     - Ponto final : Novo
     - Nome do ponto de extremidade : deixe o padrão ou certifique-se de que seja globalmente exclusivo
     - Nome da implantação : Deixe o padrão
     - Inferência de coleta de dados : Desativado
     - Modelo de pacote : Desativado

4. Após a implantação (média de ** 5 a 10 minutos**), acessei a aba **"Testar"** do ponto de extremidade.
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
