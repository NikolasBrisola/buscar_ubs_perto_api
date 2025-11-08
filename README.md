🏥 Consulta Certa - API UBS (Flask)
📘 Descrição

Esta API em Python (Flask) faz parte do projeto Consulta Certa, e tem como objetivo localizar Unidades Básicas de Saúde (UBS) próximas a partir de um CEP informado.

Ela consome dados do ViaCEP e cruza com um banco local em CSV, retornando informações simplificadas das UBS disponíveis naquela região.

⚙️ Funcionalidades

🔍 Consulta de CEP usando a API pública ViaCEP

🗺️ Busca de UBS por código IBGE no CSV local

📍 Cálculo de distância geográfica (aproximada) entre o usuário e as UBS encontradas

💾 Exportação automática dos resultados em formato JSON (ubs_resultado.json)

🌐 Suporte a CORS, permitindo uso direto por front-ends web

📁 Estrutura do Projeto
consulta-certa-ubs-api/
│
├── ubs_api.py                         # Código principal da API Flask
├── Unidades_Basicas_Saude-UBS.csv     # Base de dados local das UBS
├── requirements.txt                   # Dependências da aplicação
├── .gitignore                         # Arquivos ignorados no repositório
└── README.md                          # Este arquivo :)

🧩 Tecnologias Utilizadas

Python 3.10+

Flask (framework web)

Flask-CORS (liberação de acesso externo)

pandas (leitura e filtragem do CSV)

requests (consumo de APIs externas)

🚀 Como Executar Localmente
1️⃣ Crie um ambiente virtual (venv)
python -m venv venv
venv\Scripts\activate   # Windows
# ou no Linux/macOS:
# source venv/bin/activate

2️⃣ Instale as dependências
pip install -r requirements.txt

3️⃣ Execute a API
python ubs_api.py


A API será iniciada em:

🌐 http://127.0.0.1:5000/ubs/perto?cep=01001000

📡 Exemplo de Requisição

GET

http://127.0.0.1:5000/ubs/perto?cep=01311000
Resposta JSON:

{
    "cep": "01311-000",
    "cidade": "São Paulo",
    "uf": "SP",
    "ubs_proximas": [
        {
            "nome": "CLINICA REVELA DOR",
            "endereco": "RUA FREI CANECA, CONSOLACAO, São Paulo - SP",
            "distancia_km": 0.56
        },
        {
            "nome": "CLINICA E MICROCIRURGIA OCULAR DR IVO LUCCI FILHO",
            "endereco": "ALAMEDA MINISTRO ROCHA DE AZEVEDO, CERQUEIRA CESAR, São Paulo - SP",
            "distancia_km": 0.67
        },
        {
            "nome": "UBS NOSSA SENHORA DO BRASIL ARMANDO DARIENZO",
            "endereco": "RUA ALMIRANTE MARQUES DE LEAO, BELA VISTA, São Paulo - SP",
            "distancia_km": 1.
        }
    ]
}

☁️ Deploy no Render

Build Command:

pip install -r requirements.txt


Start Command:

gunicorn ubs_api:app


Após o deploy, a API ficará disponível em:

https://consulta-certa-ubs-api.onrender.com/ubs/perto?cep=01001000

📄 Licença

Este projeto é de uso acadêmico e faz parte da disciplina Computational Thinking Using Python (FIAP).
Pode ser reutilizado para fins de estudo e demonstração.