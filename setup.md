# ⚙️ Configuração do Ambiente de Laboratório

Este documento descreve como foi configurado o ambiente para a simulação de um ataque brute force contra um servidor **XAMPP** rodando em **Windows Server**, utilizando uma máquina **Kali Linux** como atacante.  
O objetivo é documentar todas as etapas de preparação do laboratório antes da análise de logs.

---

## 🖥️ Estrutura das Máquinas Virtuais

- **VM Alvo (Windows Server + XAMPP)**  
  - Sistema operacional: Windows Server (versão utilizada no lab)  
  - Software: XAMPP (Apache, PHP, MySQL)  
  - Função: Servidor vulnerável, alvo da simulação  
  - Logs: `C:\xampp\apache\logs\access.log`

- **VM Atacante (Kali Linux)**  
  - Sistema operacional: Kali Linux (versão utilizada no lab)  
  - Ferramentas: Nmap, Python 3  
  - Função: Simular tráfego malicioso para gerar entradas nos logs

---

## 🌐 Topologia de Rede

As duas VMs foram configuradas em **rede interna**, de forma que apenas elas se comuniquem entre si.

| Máquina   | IP utilizado     | Função         |
|-----------|-----------------|----------------|
| Windows   | 192.168.3.75  | Servidor alvo  |
| Kali      | 192.168.3.62  | Atacante       |

📸<img width="853" height="552" alt="image" src="https://github.com/user-attachments/assets/2b5ba3aa-3fca-40c3-b3ac-678448b5bd78" />

<img width="746" height="359" alt="image" src="https://github.com/user-attachments/assets/e045dee2-a9cc-4fa2-81d4-d1c3e95f6194" />

---

## 🔎 Reconhecimento com Nmap

Para identificar portas e serviços disponíveis no servidor alvo, foi utilizado o **Nmap**.  
O comando executado no Kali Linux fez a varredura de serviços e versões.

📸 <img width="741" height="636" alt="image" src="https://github.com/user-attachments/assets/72d017a2-72e4-4be4-8de1-eb3b87ee5065" />


---

## 💻 Simulação do Ataque

Foi utilizado um **script em Python** para simular requisições repetitivas ao servidor, com objetivo de gerar tentativas de autenticação mal-sucedidas e evidências em log.  
Este script não está publicado, mas foi executado localmente na VM Kali.

📸 <img width="747" height="415" alt="image" src="https://github.com/user-attachments/assets/890de59b-acae-4793-b199-ed14087292a1" />


---

## 📂 Coleta de Logs do Servidor

Após a execução do tráfego, foram coletados os arquivos de log do Apache:

- `C:\xampp\apache\logs\access.log`  

📸 <img width="996" height="676" alt="image" src="https://github.com/user-attachments/assets/2ae49cea-80e2-4ca1-991a-ffd5bbe51985" />


O arquivo `access.log` foi copiado para a pasta `evidencias/` no repositório para análise:

