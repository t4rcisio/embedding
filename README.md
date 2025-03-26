# DOC SEARCH

## Descrição
Este projeto implementa um pipeline de Recuperação Aumentada por Geração (RAG) usando vetorizadores de embeddings e um banco de dados vetorial ChromaDB. Ele permite carregar documentos em diversos formatos, dividir o conteúdo em fragmentos e indexá-los para consulta posterior.

## Requisitos

- Python 3.x
- Bibliotecas:
  - `langchain`
  - `langchain_community`
  - `langchain_text_splitters`
  - `langchain_chroma`
  - `langchain_ollama`
  - `pdfplumber`
  - `python-dotenv`
  - `ollama`
  - `shutil`

## Instalação

1. Clone este repositório:
   ```sh
   git clone <repo_url>
   cd <repo_dir>
   ```

2. Instale as dependências:
   ```sh
   pip install -r requirements.txt
   ```

3. Configure um arquivo `.env` na raiz do projeto e defina:
   ```env
   CHROMA_PATH=./chroma
   ```

## Uso

1. **Carregar arquivos e gerar o banco de vetores:**
   - Para carregar um diretório com arquivos e criar um banco de vetores para pesquisa, utilize:
   ```python
   genRAG_folder(myDir, model_id, model_name , chunk_size=300, chunk_overlap=100)
   ```

2. **Consultar a base vetorial:**
   - Para buscar informações na base vetorial:
   ```python
   response = search(model_id, "sua pergunta", k=3)
   ```

3. **Estrutura do banco vetorial:**
   - Cada banco vetorial gerado está armazenado no caminho especificado em `CHROMA_PATH` e contém:
     - `chroma.sqlite3`: Banco de dados vetorial.
     - `info.info`: Metadados do modelo utilizado.

## Funções Principais

- `checkModel(model_name)`: Verifica se o modelo está disponível localmente e faz download se necessário.
- `loadFile(file_path)`: Carrega arquivos em diferentes formatos (.pdf, .txt, .html).
- `getVector(modelID)`: Recupera um banco de vetores existente.
- `search(modelID, question, k)`: Realiza uma busca vetorial na base.
- `find_chroma_db(chroma_db_path, modelName)`: Verifica a integridade de um banco vetorial.
- `genRAG_folder(path, modelID, modelName, chunk_size, chunk_overlap)`: Processa arquivos e cria uma base vetorial.



