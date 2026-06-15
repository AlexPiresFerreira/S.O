
# ⚡ Comandos Rápidos do Linux (Cheat Sheet)

> **Tags:** #linux #comandos #cheat-sheet #referencia #rapida #terminal

---

## 📌 Visão Geral

Um guia de referência rápida para os comandos Linux mais utilizados.

🎯 **Objetivo:** Acessar rapidamente a sintaxe e o uso dos comandos essenciais.

---

## 🗂️ Navegação e Arquivos

| Comando | Descrição | Exemplo |
|---------|-----------|---------|
| `pwd` | Onde estou | `pwd` |
| `cd <dir>` | Mudar diretório | `cd /var/log`, `cd ~`, `cd ..` |
| `ls` | Listar conteúdo | `ls -la`, `ls -lh /tmp` |
| `mkdir <dir>` | Criar diretório | `mkdir -p projetos/novo` |
| `touch <file>` | Criar arquivo vazio | `touch log.txt` |
| `cp <orig> <dest>` | Copiar | `cp arquivo.txt /tmp/`, `cp -r pasta/ /backup/` |
| `mv <orig> <dest>` | Mover/Renomear | `mv antigo.txt novo.txt`, `mv arquivo.txt /destino/` |
| `rm <file>` | Remover arquivo | `rm -rf pasta/`, `rm arquivo.txt` |
| `ln -s <orig> <link>` | Link simbólico | `ln -s /var/log/syslog meu_log` |
| `cat <file>` | Ver conteúdo | `cat /etc/passwd` |
| `less <file>` | Ver paginado | `less /var/log/syslog` |
| `head -n <num> <file>` | Primeiras N linhas | `head -n 5 arquivo.txt` |
| `tail -n <num> <file>` | Últimas N linhas | `tail -n 10 arquivo.txt` |
| `tail -f <file>` | Monitorar em tempo real | `tail -f /var/log/auth.log` |
| `grep <patt> <file>` | Buscar padrão | `grep "ERROR" log.txt`, `grep -i "fail" /var/log/` |
| `find <path> -name <patt>` | Buscar arquivos | `find /home -name "*.log"` |
| `df -h` | Uso de disco | `df -h` |
| `du -sh <dir>` | Uso de diretório | `du -sh /var/log` |

---

## ⚙️ Sistema e Processos

| Comando | Descrição | Exemplo |
|---------|-----------|---------|
| `sudo <cmd>` | Executar como root | `sudo apt update` |
| `ps aux` | Listar processos | `ps aux | grep apache` |
| `top` | Monitorar processos (tempo real) | `top` |
| `htop` | Monitorar processos (interativo) | `htop` |
| `kill <PID>` | Matar processo | `kill -9 1234` |
| `killall <name>` | Matar por nome | `killall firefox` |
| `systemctl <cmd> <svc>` | Gerenciar serviços | `systemctl start apache2`, `systemctl enable ssh` |
| `journalctl -u <svc>` | Ver logs do Systemd | `journalctl -u ssh -f` |
| `crontab -e` | Editar tarefas agendadas | `crontab -e` |
| `date` | Data e hora | `date` |
| `uptime` | Tempo ligado e carga | `uptime` |
| `whoami` | Usuário atual | `whoami` |
| `id <user>` | IDs de usuário/grupo | `id alex` |
| `history` | Histórico de comandos | `history | grep ssh` |
| `clear` | Limpar tela | `clear` |

---

## 🌐 Rede

| Comando | Descrição | Exemplo |
|---------|-----------|---------|
| `ip a` | Ver IPs e interfaces | `ip a show eth0` |
| `ping <host>` | Testar conectividade | `ping google.com`, `ping -c 4 192.168.1.1` |
| `traceroute <host>` | Rota até destino | `traceroute google.com` |
| `netstat -tlnp` | Portas abertas e processos | `sudo netstat -tlnp` |
| `ss -tlnp` | Portas abertas (moderno) | `sudo ss -tlnp` |
| `dig <host>` | Consultar DNS | `dig google.com MX` |
| `host <host>` | Consultar DNS (simples) | `host google.com` |
| `nmap <ip>` | Varredura de rede | `sudo nmap -sS 192.168.1.10` |
| `ssh <user>@<host>` | Acesso remoto seguro | `ssh alex@servidor` |
| `scp <orig> <dest>` | Copiar arquivos remoto | `scp arquivo.txt alex@servidor:/tmp/` |
| `iptables -L -n -v` | Ver regras de firewall | `sudo iptables -L -n -v` |
| `tcpdump -i <iface>` | Capturar pacotes | `sudo tcpdump -i eth0 port 80` |

---

## 🔒 Segurança e Permissões

| Comando | Descrição | Exemplo |
|---------|-----------|---------|
| `chmod <perm> <file>` | Mudar permissões | `chmod 755 script.sh`, `chmod u+x script.sh` |
| `chown <user>:<group> <file>` | Mudar proprietário/grupo | `sudo chown alex:dev /var/www/` |
| `useradd <user>` | Criar usuário | `sudo useradd -m -s /bin/bash novo_user` |
| `passwd <user>` | Mudar senha | `sudo passwd novo_user` |
| `usermod -aG <group> <user>` | Add usuário a grupo | `sudo usermod -aG sudo alex` |
| `groupadd <group>` | Criar grupo | `sudo groupadd devops` |
| `chage -l <user>` | Status de expiração senha | `chage -l alex` |
| `setfacl -m u:<user>:rw <file>` | Adicionar ACL | `sudo setfacl -m u:joao:rw relatorio.txt` |
| `getfacl <file>` | Ver ACL | `getfacl relatorio.txt` |

---

## 📦 Gerenciamento de Pacotes (Debian/Ubuntu)

| Comando | Descrição | Exemplo |
|---------|-----------|---------|
| `apt update` | Atualizar lista | `sudo apt update` |
| `apt upgrade` | Atualizar pacotes | `sudo apt upgrade -y` |
| `apt install <pkg>` | Instalar pacote | `sudo apt install apache2` |
| `apt remove <pkg>` | Remover pacote | `sudo apt remove firefox` |
| `apt purge <pkg>` | Remover + configs | `sudo apt purge apache2` |
| `apt search <term>` | Buscar pacote | `apt search webserver` |
| `apt autoremove` | Remover dependências órfãs | `sudo apt autoremove` |

---

## 🐳 Docker

| Comando | Descrição | Exemplo |
|---------|-----------|---------|
| `docker pull <img:tag>` | Baixar imagem | `docker pull ubuntu:latest` |
| `docker images` | Listar imagens | `docker images` |
| `docker run -d -p <host>:<cont> <img>` | Rodar container | `docker run -d -p 8080:80 nginx` |
| `docker ps` | Listar containers rodando | `docker ps -a` |
| `docker stop <id/name>` | Parar container | `docker stop meu-nginx` |
| `docker rm <id/name>` | Remover container | `docker rm meu-nginx` |
| `docker exec -it <id/name> bash` | Entrar no container | `docker exec -it meu-nginx bash` |
| `docker-compose up -d` | Iniciar serviços (Compose) | `docker-compose up -d` |

---

## 🔗 Links Relacionados

- [[00_Index-Linux]]
- [[38_Links-Uteis]]
- [[23_Bash-Scripting]]

---

## 📚 Referências

- Linux Command Line: [linuxcommand.org](http://linuxcommand.org/)
- TLDR Pages: [tldr.sh](https://tldr.sh/)
- Explain Shell: [explainshell.com](https://explainshell.com/)
