# 🔍 Análise dos Logs de Acesso

Este documento apresenta a análise detalhada dos **logs do Apache (XAMPP)** coletados no servidor Windows após a simulação de tráfego malicioso gerado pela máquina Kali Linux.

---

## 📂 Arquivo analisado

O arquivo principal analisado foi:

/evidencias/log_apache.txt


Este log contém todos os acessos ao servidor Apache durante a simulação, incluindo requisições legítimas e maliciosas.

📸 <img width="897" height="605" alt="image" src="https://github.com/user-attachments/assets/4a0a6231-1478-483a-8ea9-a35ef9794c06" />


---

## 📌 Exemplo de Linha de Log

192.168.3.62 - - [05/Sep/2025:04:26:41 -0700] "OPTIONS / HTTP/1.1" 302 -
192.168.3.62 - - [05/Sep/2025:04:26:41 -0700] "GET /dashboard HTTP/1.1" 200 5187 "-" "Mozilla/5.0 (compatible; Nmap Scripting Engine; https://nmap.org/book/nse.html


---

## 📝 Interpretação dos Campos

Exemplo explicado:


192.168.3.62 - - [05/Sep/2025:04:26:41 -0700] "GET /dashboard HTTP/1.1" 200 5187 "-" "Mozilla/5.0 (compatible; Nmap Scripting Engine; https://nmap.org/book/nse.html
)"


- **192.168.3.62** → Endereço IP de origem (máquina Kali Linux).  
- **[05/Sep/2025:04:26:41 -0700]** → Data e hora da requisição.  
- **"GET /dashboard HTTP/1.1"** → Método HTTP, recurso solicitado e versão do protocolo.  
- **200** → Código de status (requisição bem-sucedida).  
- **5187** → Tamanho da resposta em bytes.  
- **User-Agent** → Identificado como **Nmap Scripting Engine**, confirmando que as requisições foram automatizadas.

---

## 📊 Padrões Identificados

Durante a análise, foram observados:

- **Requisições consecutivas e em alta frequência** do mesmo IP (`192.168.3.62`).  
- Diversos **métodos HTTP** utilizados (GET, POST, HEAD, OPTIONS).  
- **Status codes variados**, incluindo:  
  - `200 OK` → Requisições aceitas.  
  - `302 Found` → Redirecionamentos.  
  - `400 Bad Request` → Erros de requisição.  
  - `404 Not Found` → Tentativas de acesso a recursos inexistentes.  

---

## 🖥️ Identificação do Atacante

Foi executado o comando `ifconfig` na máquina Kali Linux.  
O IP exibido foi o mesmo registrado nos logs do Apache (`192.168.3.62`), confirmando a origem das requisições.

📸 <img width="732" height="343" alt="image" src="https://github.com/user-attachments/assets/2e7975fe-aab1-41e4-83d4-ef627dd1bd2a" />



## 🛡️ Mitigação

Após configurar o **Firewall do Windows** para bloquear o IP atacante (`192.168.3.62`):

- As requisições pararam de aparecer nos logs.  
- O servidor permaneceu acessível normalmente para outros clientes.  

📸 <img width="802" height="600" alt="image" src="https://github.com/user-attachments/assets/9e876cc3-75d0-4da7-8e28-43854a514b57" />

📸 <img width="1222" height="605" alt="image" src="https://github.com/user-attachments/assets/f46a901e-c9a1-41f6-b312-5c25ec4ed9ba" />


---

## ✅ Conclusão da Análise

- O log registrou claramente a atividade automatizada do **Nmap Scripting Engine**.  
- O padrão de múltiplos métodos HTTP, em alta frequência e do mesmo IP, é característico de varreduras e tentativas de exploração.  
- A correlação com o IP da máquina Kali confirmou a origem do tráfego.  
- A mitigação via Firewall foi eficaz em conter a origem maliciosa e preservar a disponibilidade do serviço.  


