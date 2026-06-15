
# 📜 Auditoria e Logs no Linux

> **Tags:** #linux #logs #auditoria #seguranca #journalctl #auditd #syslog #logrotate

---

## 📌 Visão Geral

Auditoria e o gerenciamento de logs são componentes críticos da segurança de sistemas, permitindo detectar atividades suspeitas, investigar incidentes e garantir conformidade.

🎯 **Objetivo:** Coletar, armazenar, analisar e proteger logs de eventos do sistema.

---

## 📊 Tipos de Logs

### Logs de Sistema

- **Kernel:** Eventos do kernel (boot, hardware, erros).
- **Serviços:** Atividade de serviços (web server, SSH, banco de dados).
- **Autenticação:** Tentativas de login, sucesso/falha.

---

### Logs de Aplicação

- Gerados por aplicações específicas (ex: logs de um servidor web, banco de dados).

---

## 🗂️ Localização dos Logs

### /var/log/

**Descrição:** Diretório padrão para a maioria dos logs do sistema.

**Arquivos comuns:**
- `/var/log/syslog` (Debian/Ubuntu): Logs gerais do sistema.
- `/var/log/messages` (Red Hat/CentOS): Logs gerais do sistema.
- `/var/log/auth.log` (Debian/Ubuntu): Logs de autenticação.
- `/var/log/secure` (Red Hat/CentOS): Logs de autenticação.
- `/var/log/kern.log`: Logs do kernel.
- `/var/log/boot.log`: Logs de inicialização.
- `/var/log/dmesg`: Mensagens do buffer do kernel.
- `/var/log/faillog`: Logs de tentativas de login falhas.
- `/var/log/lastlog`: Logs do último login de cada usuário.
- `/var/log/apache2/` ou `/var/log/nginx/`: Logs de servidores web.
- `/var/log/mysql/`: Logs do MySQL.

---

## 🔍 Visualizando Logs

### cat / less / more / head / tail

**Descrição:** Comandos básicos para visualizar o conteúdo de arquivos de log.

**Exemplos:**

bash
#### Ver conteúdo completo

cat /var/log/syslog
#### Ver paginado

less /var/log/auth.log
#### Ver últimas 10 linhas

tail /var/log/kern.log
#### Monitorar em tempo real (para logs ativos)

tail -f /var/log/auth.log


---

### grep

**Descrição:** Filtrar logs por padrões.

**Exemplos:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-kh2u1zd8m" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Buscar por erros</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">grep</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-i</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;error&quot;</span><span> /var/log/syslog
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Buscar tentativas de login falhas</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">grep</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Failed password&quot;</span><span> /var/log/auth.log
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Buscar por um IP específico</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">grep</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;192.168.1.10&quot;</span><span> /var/log/apache2/access.log
</span></code></pre></div>

---

## 📜 Systemd Journal (journalctl)

**Descrição:** Ferramenta para visualizar e gerenciar logs coletados pelo Systemd.

**Características:**
- Logs binários (não texto simples).
- Indexados e pesquisáveis por vários campos.
- Unifica logs de kernel, serviços, etc.

**Sintaxe:** `sudo journalctl [opções]`

### Opções Comuns

| Opção | Descrição |
|-------|-----------|
| `-b` | Logs do boot atual |
| `-b <id>` | Logs de um boot específico (use `journalctl --list-boots`) |
| `-f` | Seguir logs em tempo real |
| `-u <unit>` | Logs de uma unit (serviço) específica |
| `-p <priority>` | Filtrar por prioridade (emerg, alert, crit, err, warning, notice, info, debug) |
| `--since "YYYY-MM-DD HH:MM:SS"` | Logs a partir de uma data/hora |
| `--until "YYYY-MM-DD HH:MM:SS"` | Logs até uma data/hora |
| `--list-boots` | Listar todos os boots registrados |
| `--disk-usage` | Exibir uso de disco dos logs |
| `--vacuum-size=<size>` | Limpar logs antigos para liberar espaço |
| `--output=json` | Exibir logs em formato JSON |

---

### Exemplos

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-lgls2ldp5" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ver todos os logs</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> journalctl
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ver logs do boot atual</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> journalctl </span><span class="token parameter" style="color:rgb(214, 222, 235)">-b</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ver logs do boot anterior</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> journalctl </span><span class="token parameter" style="color:rgb(214, 222, 235)">-b</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-1</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Listar todos os boots</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> journalctl --list-boots
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ver logs de um serviço específico (ex: ssh)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> journalctl </span><span class="token parameter" style="color:rgb(214, 222, 235)">-u</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">ssh</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ver logs em tempo real</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> journalctl </span><span class="token parameter" style="color:rgb(214, 222, 235)">-f</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ver logs de erro</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> journalctl </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> err
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ver logs de autenticação</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> journalctl </span><span class="token assign-left" style="color:rgb(214, 222, 235)">_COMM</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span>sshd
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ver logs de um período</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> journalctl </span><span class="token parameter" style="color:rgb(214, 222, 235)">--since</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;2025-01-01 10:00:00&quot;</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">--until</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;2025-01-01 11:00:00&quot;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Limpar logs antigos (manter 1GB)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> journalctl --vacuum-size</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span>1G
</span></code></pre></div>

---

## 🛡️ Auditoria de Segurança (auditd)

**Descrição:** O framework de auditoria do kernel Linux, que registra eventos de segurança detalhados.

**Características:**
- Registra acesso a arquivos, execução de programas, chamadas de sistema.
- Essencial para conformidade (PCI-DSS, HIPAA).

**Instalação:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-zp8hgg0a0" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">apt</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">install</span><span> auditd audispd-plugins  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Debian/Ubuntu</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> yum </span><span class="token" style="color:rgb(130, 170, 255)">install</span><span> auditd audispd-plugins  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Red Hat/CentOS</span><span>
</span></code></pre></div>

**Comandos:**
- `auditctl`: Controla as regras de auditoria.
- `ausearch`: Busca em logs de auditoria.
- `aureport`: Gera relatórios de auditoria.

**Exemplos:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-qon3rlfor" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Iniciar/parar serviço</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> systemctl start auditd
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> systemctl stop auditd
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Adicionar regra para monitorar acesso a arquivo sensível</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> auditctl </span><span class="token parameter" style="color:rgb(214, 222, 235)">-w</span><span> /etc/shadow </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> rwxa </span><span class="token parameter" style="color:rgb(214, 222, 235)">-k</span><span> shadow_access
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Adicionar regra para monitorar execução de sudo</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> auditctl </span><span class="token parameter" style="color:rgb(214, 222, 235)">-a</span><span> always,exit </span><span class="token parameter" style="color:rgb(214, 222, 235)">-F</span><span> </span><span class="token assign-left" style="color:rgb(214, 222, 235)">arch</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span>b64 </span><span class="token parameter" style="color:rgb(214, 222, 235)">-S</span><span> execve </span><span class="token parameter" style="color:rgb(214, 222, 235)">-F</span><span> </span><span class="token assign-left" style="color:rgb(214, 222, 235)">euid</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span class="token" style="color:rgb(247, 140, 108)">0</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-F</span><span> </span><span class="token assign-left" style="color:rgb(214, 222, 235)">comm</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span>sudo </span><span class="token parameter" style="color:rgb(214, 222, 235)">-k</span><span> sudo_exec
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Listar regras</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> auditctl </span><span class="token parameter" style="color:rgb(214, 222, 235)">-l</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Buscar logs de auditoria</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> ausearch </span><span class="token parameter" style="color:rgb(214, 222, 235)">-k</span><span> shadow_access
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> ausearch </span><span class="token parameter" style="color:rgb(214, 222, 235)">-m</span><span> USER_LOGIN
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Gerar relatório de falhas de autenticação</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> aureport </span><span class="token parameter" style="color:rgb(214, 222, 235)">-au</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">--failed</span><span>
</span></code></pre></div>

---

## 🔄 Rotação de Logs (logrotate)

**Descrição:** Gerencia a rotação, compressão e remoção de arquivos de log.

**Características:**
- Evita que arquivos de log cresçam indefinidamente e consumam espaço em disco.
- Configurado em `/etc/logrotate.conf` e `/etc/logrotate.d/`.

**Exemplo de configuração (`/etc/logrotate.d/apache2`):**
```

/var/log/apache2/*.log { daily # Rotacionar diariamente missingok # Não gerar erro se o log não existir rotate 14 # Manter 14 arquivos rotacionados compress # Comprimir logs antigos delaycompress # Comprimir apenas a partir do segundo ciclo notifempty # Não rotacionar se o arquivo estiver vazio create 0640 root adm # Criar novo arquivo com permissões sharedscripts # Executar scripts apenas uma vez por ciclo postrotate # Script a ser executado após a rotação /usr/sbin/apache2ctl graceful > /dev/null endscript }

```
**Uso:**
- `logrotate` é executado automaticamente pelo `cron` (geralmente via `/etc/cron.daily/logrotate`).
- `sudo logrotate -f /etc/logrotate.conf` (forçar rotação manual).
- `sudo logrotate -d /etc/logrotate.conf` (modo debug).

---

## 🔗 Links Relacionados

- [[12_Systemd-e-Servicos]]
- [[23_Bash-Scripting]]
- [[24_AWK-Avancado]]
- [[19_Hardening-Linux]]
- [[04_Gerenciamento-de-Arquivos]]

---

## 📚 Referências

- Journalctl Man Page: [man7.org/linux/man-pages/man1/journalctl.1.html](https://man7.org/linux/man-pages/man1/journalctl.1.html)
- Auditd Man Page: [man7.org/linux/man-pages/man8/auditd.8.html](https://man7.org/linux/man-pages/man8/auditd.8.html)
- Logrotate Man Page: [man7.org/linux/man-pages/man8/logrotate.8.html](https://man7.org/linux/man-pages/man8/logrotate.8.html)
- Rsyslog: [www.rsyslog.com](https://www.rsyslog.com/)
