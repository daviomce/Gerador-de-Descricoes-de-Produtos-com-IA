# Gerador de Descrições de Produtos com IA

Este projeto utiliza a API do Gemini da Google para gerar descrições de produtos otimizadas para e-commerce a partir de imagens e informações adicionais fornecidas pelo usuário. Ele automatiza o processo de criação de conteúdo persuasivo e informativo, economizando tempo e esforço.

## Funcionalidades

* [cite_start] **Geração de Descrições a partir de Imagens:** A IA analisa a imagem do produto para identificar suas características visuais.
* [cite_start] **Entrada de Informações Adicionais:** O usuário pode fornecer informações como nome do produto, marca, público-alvo e características-chave.
* [cite_start] **Seleção de Tom de Voz:** O usuário pode escolher o tom da descrição (amigável, formal, técnico, etc.) para adequá-la ao público e ao contexto.
* **Otimização para SEO:** As descrições são geradas com foco em palavras-chave relevantes para melhorar a visibilidade nos mecanismos de busca.
* [cite_start] **Salvamento em PDF:** A descrição gerada, juntamente com a imagem do produto, pode ser salva em um arquivo PDF no Google Drive.
* **Organização:** Os arquivos PDF são salvos em uma pasta específica ("Gerador\_de\_descricao") no Google Drive para fácil organização.

## Como Usar

1.  **Pré-requisitos**

    * Uma conta no Google Cloud e um projeto com a API do Gemini habilitada.
    * A chave da API do Gemini configurada nos "Segredos" do Google Colab.
    * Google Drive montado no Google Colab.

2.  **Instalação**

    * Abra o notebook no Google Colab.
    * Execute a primeira célula para instalar as bibliotecas necessárias:
        ```python
        !pip install -q google-generativeai pillow python-dotenv fpdf2
        ```

3.  **Execução**

    * Execute as células do notebook na ordem.
    * Faça o upload da imagem do produto quando solicitado.
    * Forneça as informações adicionais do produto (nome, marca, público-alvo, etc.).
    * Escolha o tom de voz desejado para a descrição.
    * A descrição gerada será exibida e salva em um arquivo PDF no seu Google Drive, na pasta "Gerador\_de\_descricao".

## Código Exemplo

Aqui está um trecho de código que demonstra como a descrição é gerada e salva:

```python
def salvar_pdf_no_drive(imagem_bytes, descricao, titulo, caminho_base='/content/drive/MyDrive/Gerador_de_descricao/'):
    # ... (código da função para salvar o PDF)

generated_description = generate_description_with_gemini(pil_image_obj, full_prompt)
if generated_description:
    titulo_para_arquivo = generated_description.split('\n')[0].replace('**', '').strip()
    salvar_pdf_no_drive(image_bytes, generated_description, titulo_para_arquivo)
