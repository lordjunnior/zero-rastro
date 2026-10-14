---
titulo: "Roteamento Cebola e Navegação Desvinculada"
descricao: "Como funciona a rede Tor, como configurar o navegador oficial e quais as regras operacionais para quebrar a correlação de tráfego."
---

# Roteamento Cebola: Navegação Desvinculada de Identidade

Navegadores comuns e conexões convencionais entregam seu endereço IP real a cada site acessado. Redes virtuais privadas (VPNs) tradicionais apenas trocam quem enxerga seu tráfego: seu provedor de internet deixa de ver, mas a empresa da VPN passa a registrar tudo em servidores centrais.

Para quebrar a cadeia de custódia da conexão, a solução técnica auditada é o roteamento em camadas (Onion Routing) da rede Tor.

---

## 1. Como a Rede Tor Funciona na Prática

Ao navegar pelo Navegador Tor, sua conexão não vai direto ao destino:
1. Nó de Entrada (Guard Node): Conhece o seu endereço IP real, mas não sabe o que você está acessando nem qual é o site de destino.
2. Nó Intermediário (Middle Relay): Repassa o pacote cifrado sem conhecer a origem nem o destino final.
3. Nó de Saída (Exit Node): Entrega o pacote ao site final, mas não sabe quem você é nem de onde a conexão partiu.

Nenhum computador individual no circuito possui a informação completa do caminho. Isso torna a análise de tráfego por provedores e governos extremamente custosa e estatisticamente ineficaz.

---

## 2. Instalação e Verificação de Integridade

Nunca utilize versões modificadas ou aplicativos de terceiros que afirmam "acelerar o Tor". Utilize apenas o cliente oficial mantido pelo projeto:

1. Baixe o pacote oficial para seu sistema operacional.
2. Verifique a assinatura OpenPGP do arquivo de instalação antes de executar:
   ```bash
   gpg --verify tor-browser-*.tar.xz.asc