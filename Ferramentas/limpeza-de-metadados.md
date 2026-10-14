---
titulo: "Higienização de Arquivos e Destruição de Metadados"
descricao: "Como remover rastros de geolocalização, números de série de câmeras e históricos de edição de imagens e documentos antes de qualquer envio."
---

# Higienização de Arquivos e Destruição de Metadados

Toda vez que você tira uma foto com o celular, exporta um PDF ou salva um arquivo de texto, o software grava silenciosamente uma camada invisível de dados: os **metadados** (como tags EXIF).

Esses dados entregam:
* Coordenadas exatas de GPS de onde a foto foi tirada (com precisão de metros).
* Data, hora e fuso horário do registro.
* Modelo exato do aparelho, fabricante e versão do sistema operacional.
* Número de série da câmera ou lente.
* Histórico de programas usados na edição e nomes de contas locais no computador.

Mesmo que você compartilhe um arquivo de forma anônima, os metadados internos denunciam sua identidade e localização física. A sanitização prévia é o primeiro passo de qualquer procedimento de segurança.

---

## 1. Ferramentas Recomendadas para Limpeza Local

Não use sites de terceiros para "limpar fotos online". Enviar seus arquivos para um servidor web derrota todo o propósito de privacidade. A limpeza precisa ser feita localmente na sua máquina:

* **Limpador de Metadados (Metadata Cleaner):** Interface visual leve para ambientes Linux, baseada na biblioteca `mat2`. Permite arrastar pastas inteiras e limpar fotos, vídeos, PDFs e áudios em lote com um clique.
* **ExifTool (Terminal / Automação):** A ferramenta mais poderosa e auditada do mundo para leitura e destruição cirúrgica de metadados em qualquer sistema operacional (Linux, Windows, macOS).

---

## 2. Como Fazer a Limpeza no Computador

### Opção A: Limpeza Visual Simples (Interface Gráfica)
1. Instale o utilitário local de limpeza de metadados.
2. Arraste os arquivos desejados para dentro da janela do programa.
3. Clique em **Limpar**.
4. O aplicativo gera uma cópia limpa do arquivo, destruindo coordenadas de GPS, dados de câmera e assinaturas de software, mantendo apenas os pixels visíveis da imagem ou o texto do documento.

### Opção B: Destruição Cirúrgica via Linha de Comando (ExifTool)
Para quem opera via terminal e precisa sanitizar diretórios inteiros rapidamente sem deixar sobras:

* **Inspecionar os rastros ocultos de um arquivo:**
  ```bash
  exiftool arquivo.jpg