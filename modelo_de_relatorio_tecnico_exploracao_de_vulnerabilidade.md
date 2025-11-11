# Relatório de Exploração de Vulnerabilidade

---
<br>
<p align="center">
  <img src="https://img.shields.io/static/v1?label=DIO&message=Education&color=E94D5F&labelColor=202024" alt="DIO Project" />
</p>

---

<!--  -->
<table align="center">
<thead>
  <tr>
    <td>
        <p align="center">Aluno</p>
        <a href="https://github.com/marcelonascimento22">
        <img src="https://avatars.githubusercontent.com/u/18772730?s=400&u=aee6958019380bf2a08057e8bc05c524ce5ba923&v=4" alt="@felipeAguiarCode"><br>
      </a>
    </td>
    <td colspan="3">
    <p> Estou me reinventando e iniciando minha carreira como Desenvolvedor, determinado a transformar minha paixão em resultados concretos e impacto positivo.
      <br/>
     🌟 Desenvolvedor backend
      <br/>
    👨‍💻 Foco em DevSecOps
    </p>
      <a 
      href="https://www.linkedin.com/in/marcelo12nascimento/" 
      align="center">
           <img 
            align="center" 
            alt="Material de Apoio" 
            src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white"
            >
        </a>
    </td>
  </tr>
</thead>
</table>

---

## 📌 1. Informações Gerais
**Título:** Relatório de Exploração de Vulnerabilidade  
**Projeto/Sistema:** Metasploitable 2 e DVWA  
**Cliente:** DIO  
**Responsáveis:** Marcelo Nascimento  
**Versão:** v1.0

---

## 🎯 2. Escopo e Regras de Engajamento
**Escopo autorizado:**  
- Hosts/IPs: 192.168.56.101  
- Endpoints: Metasploitable 2 / VirtualBox  

**Atividades permitidas:**  
- Varredura ativa  
- Testes de intrusão controlados  
- Validação manual   
---

## 🧭 3. Fases

- Reconhecimento
- Enumeração 
- Análise
- Exploração 
- Evidências 
- Report

---

## 🖥️ 4. Ambiente de Teste
- Ambiente: Metasploitable 2 / VirtualBox    
- Credenciais de teste: _preencher_  

---

## 🔧 5. Ferramentas Utilizadas
- **arp-scan:** Escaneia a rede LAN usando o protocolo ARP para descobrir dispositivos ativos
- **Nmap:** Escaneia redes e hosts para identificar dispositivos, verificar portas abertas, detectar serviços e sistemas operacionais  
- **Medusa:** Ferramenta para realizar ataques de força bruta rápidos e eficientes contra diversos serviços de rede, como HTTP, FTP, SSH, Telnet, POP3, IMAP, VNC, entre outros 
- **enum4linux:** Para realizar enumeração de informações em sistemas operacionais Windows e Linux (que utilizam o Samba), para coletar dados sobre um alvo e identificar potenciais vulnerabilidades

---

## 📊 6. Resumo das Vulnerabilidades
| ID | Porta | Serviço| Vulnerabilidade | Severidade | Status | Observações |
|----|-------|--------|-----------------|------------|--------|-------------|
| V‑001 | 21 | FTP | Brute Force | Crítica | Confirmada | Exposição de dados |
V‑002 | 80 | HTTP | Brute Force | Crítica | Confirmada | Exposição de dados |
V‑003 | 445 | SMB | Ataque em Cadeia | Crítica | Confirmada | Exposição de dados |



---

## 🕵️ 7. Detalhamento das Vulnerabilidades
### Exploração
**Coleta de informações relevantes:** 

**I -** Varredura da Rede com objetivo de descobrir o IP do host alvo.
<img align="center"  
    src="./images/Captura de tela 2025-11-10 003823.png"
    >

**II -** Scaneando os serviços abertos no host alvo.
<img align="center"  
    src="./images/Captura de tela 2025-11-10 004110.png"
    >

### Preparação
**Criando as word list:** 

**I -** Possíveis usuários  e senhas.
<img align="center"  
    src="./images/Captura de tela 2025-11-10 004612.png"
    >


### V‑001 Brute Force no serviço FTP
**Descrição:**  
**I -** Usando a Medusa para realizar as combinações de forma automatizada.
<img align="center"  
    src="./images/Captura de tela 2025-11-10 004654.png"
    >

**II -** Resultado do teste.
<img align="center"  
    src="./images/Captura de tela 2025-11-10 004811.png"
    >

**III -** Analisando o resultado temos a combinação de msfadmin para usuário e senha com sucesso.
<img align="center"  
    src="./images/Captura de tela 2025-11-10 004811.png"
    >

**IV -** Validando o resultado.
<img align="center"  
    src="./images/Captura de tela 2025-11-10 005249.png"
    >

**IV -** Exfiltração de dados.
<img align="center"  
    src="./images/Captura de tela 2025-11-10 005515.png"
    >

**IV -** Abrindo o dado vazado.
<img align="center"  
    src="./images/Captura de tela 2025-11-10 005619.png"
    >

### V‑002 Brute Force no servidor Web
**Descrição:** 
**I -** Analisando a Resquest do método POST e o retorno do login.
<img align="center"  
    src="./images/Captura de tela 2025-11-10 005942.png"
    >

**II -** Realizando ataque novamente com a medusa e as word lists e analisando o resultado.
<img align="center"  
    src="./images/Captura de tela 2025-11-10 010342.png"
    >

**III -** Validando o resultado do teste.
<img align="center"  
    src="./images/Captura de tela 2025-11-10 010428.png"
    >


### V‑003 Brute Force no serviço de rede SMB
**Descrição:** 
**I -** Realizando a enumeração dos possíveis usuários.
<img align="center"  
    src="./images/Captura de tela 2025-11-10 011716.png"
    >

<img align="center"  
    src="./images/Captura de tela 2025-11-10 011802.png"
    >

**II -** Criando uma nova word list com base na análise do resultado do Enum4linux.

- Lista de Usuários:

<img align="center"  
    src="./images/Captura de tela 2025-11-10 171433.png"
    >

- Lista de Senhas:

<img align="center"  
    src="./images/Captura de tela 2025-11-10 171307.png"
    >

**III -** Realizando ataque com a Medusa e analisando os resultados do teste.

<img align="center"  
    src="./images/Captura de tela 2025-11-10 172554.png"
    >

**IV -** Validando o resultado do teste automatizado.

<img align="center"  
    src="./images/Captura de tela 2025-11-10 172819.png"
    >

### Analisando todos os serviços do Host Alvo para ações futuras.
**Descrição:** 
**I -** Usando o nmap para realizar varredura de todas as portas abertas.
<img align="center"  
    src="./images/Captura de tela 2025-11-10 181001.png"
    >

**Local/Vetor:**  
```
192.168.56.101 / Metasploitable 2 (VirtualBox)
```

**Evidência (PoC conceitual):**  
- O serviço FTP e o formulário de login não implementam mecanismos de bloqueio após múltiplas tentativas de acesso falhas provenientes do mesmo endereço IP, permitindo tentativas sucessivas de autenticação sem qualquer restrição.

**Impacto:**  
- Tomada de conta (Account takeover)

- Invasor acessa contas válidas (usuário/senha), usando-as para operações legítimas, mudança de credenciais ou persistência.

- Exfiltração de dados

- Distribuição de malware / plantio de backdoor

- Upload via FTP (se permitido) de webshells, malware ou scripts de persistência.

- Movimentação lateral e escalonamento de privilégios

- Contas comprometidas podem ser pivot usadas para alcançar outras máquinas/serviços internos.

- Fraude e abuso de serviços

- Uso indevido de contas para enviar e-mails, transações financeiras, ou modificar conteúdo público.

- Interrupção de serviço / DoS local

- Reputação e impactos legais

- Vazamento de dados pode gerar perda de confiança, multas regulatórias e obrigações de notificação.

- Bloqueio de usuários legítimos


**Recomendações:**  
- Implementar rate limiting por IP (ex.: X tentativas por minuto).

- Aplicar bloqueio temporário/cooldown após N tentativas falhas (ex.: 5 falhas → bloqueio 15 min).

- Habilitar MFA para contas com privilégios.

- Adotar CAPTCHA em formulários de login para reduzir automação.

- Impedir upload via FTP para contas que não precisem; se necessário, restringir por ACLs.

- Instalar/ativar ferramentas como fail2ban para bloquear IPs que repetem falhas.

- Regras WAF para detectar e bloquear padrões de força-brute/credential stuffing.


---

## ✅ 10. Recomendações Gerais
- Aplicar patches pendentes  
- Implementar headers de segurança  
- Ativar logs e alertas contínuos  
- Revisar privilégios de usuários  
- Harden do servidor

---

## 📎 11. Anexos
- [Word list de usuários](./arquivos/users.txt)  
- [Word list de senhas](./arquivos/pass.txt)
- [Word list de usuários smb](./arquivos/smb_users.txt)  
- [Word list de senhas smb](./arquivos/senhas_spray.txt) 
- [Saídas do Enum4linux](./arquivos/enum4_output.txt)  

---

