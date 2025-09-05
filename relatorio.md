# Relatório de Simulação de Ataque Brute Force em Servidor XAMPP

**Data:** 05/09/2025  
**Autor:** Vanessa Maciel Ferreira  
**Projeto:** Laboratório de Cibersegurança – Brute Force XAMPP  

> ⚠️ **Aviso:** Este relatório documenta atividades em ambiente de laboratório controlado, com finalidade exclusivamente educacional. Nenhuma ação ilegal foi conduzida.

## 1. Resumo Executivo
Em 05/09/2025, foi realizada uma simulação de ataque **brute force** contra um servidor **XAMPP** rodando em **Windows Server**, utilizando uma máquina **Kali Linux** como atacante. O experimento teve como objetivo analisar os logs de acesso do Apache, identificar padrões de ataque e aplicar medidas de mitigação. O ataque gerou múltiplas tentativas de login falhas em curto intervalo de tempo, confirmadas pelo log Apache. A mitigação via firewall demonstrou sucesso, mantendo a disponibilidade do servidor.

## 2. Escopo do Experimento
- **Ambiente Alvo:** Windows Server com XAMPP  
- **Ambiente Atacante:** Kali Linux  
- **Endpoint Focado:** `/login.php`  
- **Ferramentas de Reconhecimento:** Nmap (mapeamento de portas e serviços)  
- **Ferramenta de Simulação de Ataque:** Script Python seguro (gerou requisições simuladas)  
- **Logs Analisados:** `C:\xampp\apache\logs\access.log`  
- **Objetivo:** Avaliar padrões de ataque, consolidar análise de logs e testar mitigação via firewall.  


## 3. Linha do Tempo (Timeline)
| Horário | Evento |
|---------|-------|
| 4:30   | Início do reconhecimento de portas (Nmap) |
| 4:32   | Início do ataque simulado (Python script) |
| 4:38   | Coleta do arquivo `access.log` |
| 4:43   | Análise dos logs identificando padrões de brute force |
| 5:02   | Aplicação do bloqueio via firewall no Windows Server |
| 5:08   | Teste pós-mitigação: serviço permaneceu acessível |
| 5:310   | Finalização do experimento e documentação |

## 4. Descrição Técnica
### 4.1 Reconhecimento
Comando utilizado (somente para registro, ambiente seguro):
```bash
nmap -sV -A -T5 <IP_SERVIDOR>
python3 vane_dos.py
ifconfig

O experimento confirmou que ataques de brute force podem ser facilmente detectados através de análise de logs. A mitigação via firewall demonstrou eficácia em manter a disponibilidade do serviço. O exercício reforça a importância de monitoramento contínuo, análise de padrões de ataque e implementação de mecanismos de defesa automatizados.
