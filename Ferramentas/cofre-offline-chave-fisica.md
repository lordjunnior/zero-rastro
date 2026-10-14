---
titulo: "Cofre Offline com Desafio-Resposta em Chave Fisica"
descricao: "Procedimento completo para criacao e gestao de credenciais locais com KeePassXC blindado por YubiKey via HMAC-SHA1."
---

# Cofre Offline com Chave Fisica: KeePassXC + YubiKey

Armazenar senhas em nuvens comerciais cria um ponto unico de falha. Se o servidor for comprometido, seu cofre cifrado fica vulneravel a ataques de forca bruta offline.

A gestao segura de credenciais baseia-se em dois principios:
1. Banco de dados local: O arquivo do cofre (.kdbx) permanece sob sua posse fisica.
2. Segundo fator em hardware: O cofre exige a senha mestre combinada com uma resposta criptografica gerada dentro de um chip fisico nao extraivel.

---

## 1. Funcionamento do Desafio-Resposta (HMAC-SHA1)

Diferente de um codigo descartavel de celular (TOTP), o protocolo de Desafio-Resposta (Challenge-Response) funciona de forma ativa:
* O KeePassXC envia um desafio matematico para a chave fisica conectada na porta USB.
* O processador interno da chave calcula a resposta usando uma chave secreta gravada em hardware.
* O cofre so decodifica o banco de dados se a senha digitada e a resposta do chip coincidirem.

Se um invasor copiar o seu arquivo .kdbx, nao conseguira abri-lo sem a chave fisica. Se roubarem a sua chave fisica, ela e inutil sem a sua senha mestre memorizada.

---

## 2. Preparacao do Hardware (YubiKey Manager)

1. Insira a chave fisica no computador.
2. Abra o utilitario YubiKey Manager.
3. Navegue ate Applications > OTP.
4. No Slot 2, clique em Configure (o Slot 1 costuma vir reservado para autenticacoes rapidas de fabrica).
5. Selecione a opcao Challenge-response.
6. Clique em Generate para criar a chave secreta (Secret Key) de 20 bytes.
7. PROCEDIMENTO CRITICO: Copie essa sequencia hexadecimal e anote-a fisicamente em um local seguro. Ela sera usada para clonar a chave reserva.
8. Marque a caixa Require touch para exigir toque fisico no sensor a cada abertura.
9. Clique em Finish para gravar o segredo no circuito da chave.

---

## 3. Criacao do Cofre no KeePassXC

1. Abra o KeePassXC e selecione Criar novo banco de dados.
2. Defina o nome do arquivo e o diretorio local no disco onde ele ficara guardado.
3. Configure os parametros de seguranca do banco:
   * Algoritmo de cifra: ChaCha20 ou AES-256.
   * Derivacao de chave (KDF): Argon2id (configure o teste de benchmark para 1 segundo de calculo por tentativa).
4. Na tela de definicao da Chave Mestra:
   * Defina uma senha longa (recomenda-se o metodo Diceware com 6 ou mais palavras).
   * Abra a aba Opcoes Avancadas e marque Chave de Seguranca (YubiKey).
   * Clique no botao de deteccao para localizar o dispositivo USB.
   * Selecione o Slot 2.
5. Conclua o processo e encoste no sensor fisico da chave para finalizar a gravacao.

---

## 4. Politica de Redundancia e Backup

A perda da chave fisica sem chave reserva configurada resulta em bloqueio permanente do cofre. Para evitar esse risco:

### Clonagem da Chave Reserva
1. Insira a segunda chave de seguranca.
2. No YubiKey Manager, configure o Slot 2 no modo Challenge-response.
3. Em vez de gerar um novo codigo, cole exatamente o mesmo segredo hexadecimal anotado no Passo 2.
4. Grave a configuracao. Agora, ambas as chaves fisicas abrem o mesmo cofre de forma identica.

### Copia Segura do Banco (.kdbx)
Como o arquivo esta protegido por criptografia de alta densidade e exige a chave fisica, voce pode manter copias do arquivo .kdbx em midias fisicas desconectadas (como pendrives secundarios ou cartoes de memoria).