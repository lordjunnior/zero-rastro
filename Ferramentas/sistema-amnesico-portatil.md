---
titulo: "Sistema Operacional Amnésico em Mídia Removível (Tails)"
descricao: "Guia tático para inicialização de computadores a partir de um sistema descartável que não deixa registros em disco."
---

# Sistema Amnésico Portátil: Operações em Ambientes Hostis

Sistemas operacionais convencionais (Windows, macOS e distribuições comuns de Linux) foram desenhados para persistência: registram logs de execução, arquivos temporários, caches de navegação, registros de hardware e conexões de rede no disco local.

Em cenários que exigem isolamento absoluto, o **Tails (The Amnesic Incognito Live System)** resolve essa exposição operando em modo volátil.

---

## 1. Princípios de Segurança do Sistema

* **Execução exclusiva em memória RAM:** O sistema roda diretamente da memória volátil do computador. Nada é lido ou gravado no disco rígido ou SSD da máquina hospedeira.
* **Amnésia completa no encerramento:** Ao desligar ou remover o pendrive, a memória RAM perde a alimentação elétrica e todo o histórico da sessão é apagado sem deixar vestígios para perícia forense.
* **Túnel de rede obrigatório:** Todas as conexões de saída são forçadas através da rede Tor. Conexões diretas que tentem ignorar a criptografia de roteamento são bloqueadas pelo firewall nativo.

---

## 2. Preparação da Mídia de Instalação

### Requisitos Mínimos
* Um pendrive com capacidade mínima de 8 GB (que será formatado integralmente).
* O arquivo de imagem oficial (`.img`) baixado do portal do projeto.
* Assinatura criptográfica OpenPGP da imagem para validação de integridade.

### Procedimento de Gravação
1. Baixe o arquivo de imagem e sua respectiva chave de assinatura.
2. Verifique a integridade do arquivo antes da gravação para garantir que não houve adulteração no download:
   ```bash
   gpg --verify tails-amd64-*.img.sig