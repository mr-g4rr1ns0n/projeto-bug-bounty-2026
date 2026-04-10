# Semana 01 - Introdução a Redes de Computadores

**Data:** 09 a 12 de Abril de 2026  
**Livro:** TCP/IP PARA PENTESTERS (páginas 3 a 9)  
**Status:** ✅ Concluída

## Objetivo da Semana
Entender os conceitos básicos de redes que são a base para todo o bug bounty e pentest.

## Resumo do que estudei (páginas 3–9)

### 1. Conceitos Básicos de Rede
- Uma **rede de computadores** é a comunicação entre dois ou mais computadores (hosts) que trocam informações.
- Cada computador na rede pode ser:
  - **Cliente**: consome serviços (ex: navegador acessando um site)
  - **Servidor**: oferece serviços (ex: servidor web que entrega o site)

### 2. Protocolos
- Computadores diferentes (Windows, Linux, macOS, etc.) conseguem se comunicar graças aos **protocolos**.
- O principal protocolo usado hoje é o **TCP/IP**.

### 3. Elementos necessários para a comunicação
Para dois hosts se comunicarem precisamos de três coisas:

| Elemento              | Nome              | Função                                      | Exemplo                          |
|-----------------------|-------------------|---------------------------------------------|----------------------------------|
| Endereço Físico       | MAC Address       | Identificação única da placa de rede        | a4:5e:60:b8:c1:af                |
| Endereço Lógico       | IP Address        | Endereço atribuído pela rede                | 192.168.0.102                    |
| Porta                 | Port              | "Porta" usada para identificar o serviço    | 80 (HTTP), 443 (HTTPS), 22 (SSH) |

### 4. MAC Address
- É único de fábrica (6 bytes).
- Os 3 primeiros bytes identificam o fabricante.
- Podemos alterar facilmente com o comando `macchanger` (MAC Spoofing).
- Útil para bypass de controles de rede e anonimato.

### 5. Portas
- Vão de 0 a 65535.
- Portas baixas (1-1023) são bem conhecidas (ex: 80, 443, 22).
- Clientes usam portas altas e aleatórias.
- Servidores usam portas fixas.

### 6. Exemplo prático da comunicação
Cliente (MacBook) → Servidor Web (Linux)
- Cliente: MAC `a4:5e:60:b8:c1:af` | IP `192.168.0.102` | Porta `50234`
- Servidor: MAC `00:0c:29:76:43:e1` | IP `192.168.0.200` | Porta `80`

## Comandos que pratiquei

```bash
ip a                    # ver IP e MAC atual
macchanger -s eth0      # ver MAC atual
sudo macchanger -r eth0 # trocar MAC por aleatório
sudo macchanger -p eth0 # voltar MAC original
ss -tuln                # ver portas abertas na máquina
