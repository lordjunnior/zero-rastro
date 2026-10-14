---
titulo: "Documentos e Notas Cifradas com Zero Conhecimento"
descricao: "Uso de suites de escritorio colaborativas onde a criptografia ocorre no navegador antes do envio ao servidor."
---

# Documentos Cifrados: Edicao Colaborativa Sem Intermediarios

Utilizar suites de escritorio convencionais significa entregar o texto bruto de notas, contratos e rascunhos para servidores que indexam e analisam o conteudo em tempo real.

O modelo de Zero Conhecimento (Zero-Knowledge) inverte essa logica atraves da criptografia no lado do cliente (client-side)[cite: 2].

---

## 1. Arquitetura da Criptografia no Navegador

Plataformas baseadas em software livre como o CryptPad operam sob um principio matematico estrito[cite: 2]:
* Todo documento (texto, planilha, apresentacao ou codigo) e cifrado pelo proprio navegador usando chaves criptograficas geradas localmente[cite: 2].
* O que e transmitido e guardado no servidor e um amontoado ilegivel de bytes cifrados[cite: 2].
* A chave de decodificacao fica embutida no fragmento da URL (o trecho apos o caractere #), que por padrao de protocolo web nunca e enviado aos servidores de hospedagem[cite: 2].

Mesmo que os administradores do servidor sofram invasao ou apreensao dos discos, eles nao conseguem ler o conteudo dos arquivos armazenados[cite: 2].

---

## 2. Criacao e Operacao de Documentos

1. Acesse uma instancia auditada do servico ou hospede a sua propria em infraestrutura autonoma[cite: 2].
2. E possivel utilizar a plataforma no Modo Anonimo (sem cadastro, sem e-mail, sem dados pessoais)[cite: 2]. Documentos anonimos possuem prazo de expiracao automatico se ficarem inativos[cite: 2].
3. Para manter documentos permanentes sob controle, crie uma conta usando apenas Nome de Usuario e Senha Mestra[cite: 2].
   * Nao existe recuperacao de senha por e-mail[cite: 2]. Se perder a senha mestre, o acesso aos arquivos e irrecuperavel[cite: 2].

---

## 3. Compartilhamento e Controle de Acesso

Ao compartilhar um arquivo com parceiros ou equipe[cite: 2]:
* Link de Leitura: Envia a chave necessaria apenas para decodificar e ler o texto em tela[cite: 2].
* Link de Edicao: Permite alteracao colaborativa simultanea em tempo real via canais cifrados[cite: 2].
* Definicao de Senha Adicional: E possivel adicionar uma camada extra de senha ao link para impedir que pessoas que interceptem o link consigam abrir o arquivo[cite: 2].

---

## 4. Rotina de Exportacao e Destruicao

Servicos web de edicao devem ser tratados como ambientes transitorios:
* Concluido o trabalho colaborativo, exporte o documento bruto para o seu disco local (.md, .odt, .csv)[cite: 2].
* Apague o documento da instancia remota para limpar os blocos cifrados do historico[cite: 2].