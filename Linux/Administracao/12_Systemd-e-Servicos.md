
# ⚙️ Systemd e Gerenciamento de Serviços

> **Tags:** #linux #systemd #servicos #administracao #boot #daemon

---

## 📌 Visão Geral

**Systemd** é o sistema de inicialização (init system) e gerenciador de serviços padrão na maioria das distribuições Linux modernas.

🎯 **Objetivo:** Gerenciar o ciclo de vida dos serviços do sistema, desde a inicialização até o desligamento.

---

## 📜 História dos Init Systems

### SysVinit (System V Init)

**Descrição:** O sistema init tradicional, baseado em scripts sequenciais.

**Características:**
- Processos iniciados em série.
- Scripts em `/etc/init.d/`.
- Níveis de execução (runlevels).

---

### Upstart

**Descrição:** Desenvolvido pela Canonical (Ubuntu), tentou modernizar o SysVinit.

**Características:**
- Baseado em eventos.
- Mais rápido que SysVinit.
- Substituído pelo Systemd.

---

### Systemd

**Descrição:** O sistema init e gerenciador de serviços atual.

**Características:**
- Inicia processos em paralelo (mais rápido).
- Gerencia serviços, sockets, dispositivos, pontos de montagem, etc.
- Usa "units" para descrever serviços.
- Registra logs com `journalctl`.

---

## 📊 Componentes do Systemd

### PID 1

**Descrição:** O processo `systemd` é o primeiro a ser iniciado pelo kernel (PID 1). Ele é o pai de todos os outros processos.

bash ps -p 1 -o comm=


---

### Units

**Descrição:** Arquivos de configuração que descrevem como o Systemd deve gerenciar um recurso.

**Tipos de Units:**
- `.service`: Serviços (ex: `apache2.service`)
- `.socket`: Sockets de rede ou IPC
- `.device`: Dispositivos de kernel
- `.mount`: Pontos de montagem
- `.target`: Grupos de units (ex: `multi-user.target`)
- `.timer`: Agendamento de tarefas (alternativa ao Cron)

**Localização dos arquivos de unit:**
- `/etc/systemd/system/`: Criados/modificados pelo administrador.
- `/usr/lib/systemd/system/`: Fornecidos pelos pacotes.

---

## 🚀 Gerenciando Serviços (systemctl)

**Descrição:** Comando principal para controlar o Systemd.

### Sintaxe Básica

`sudo systemctl [comando] [unit_name]`

---

### Comandos Comuns

| Comando | Descrição |
|---------|-----------|
| `start` | Iniciar serviço |
| `stop` | Parar serviço |
| `restart` | Reiniciar serviço |
| `reload` | Recarregar configuração (sem parar o serviço) |
| `status` | Exibir status do serviço |
| `enable` | Habilitar serviço para iniciar no boot |
| `disable` | Desabilitar serviço para não iniciar no boot |
| `is-enabled` | Verificar se o serviço está habilitado |
| `is-active` | Verificar se o serviço está ativo |
| `show` | Exibir propriedades detalhadas da unit |
| `list-units` | Listar units carregadas |
| `list-unit-files` | Listar todos os arquivos de unit |
| `list-dependencies` | Listar dependências de uma unit |
| `daemon-reload` | Recarregar arquivos de unit após modificação |

---

### Exemplos

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-qwbqp1fd4" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Iniciar Apache</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> systemctl start apache2
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Parar SSH</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> systemctl stop </span><span class="token" style="color:rgb(130, 170, 255)">ssh</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Reiniciar MySQL</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> systemctl restart mysql
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Recarregar Nginx</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> systemctl reload nginx
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ver status do Apache</span><span>
</span>systemctl status apache2
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Habilitar SSH no boot</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> systemctl </span><span class="token" style="color:rgb(255, 203, 139)">enable</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">ssh</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Desabilitar Apache no boot</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> systemctl disable apache2
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar se SSH está habilitado</span><span>
</span><span>systemctl is-enabled </span><span class="token" style="color:rgb(130, 170, 255)">ssh</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar se Apache está ativo</span><span>
</span>systemctl is-active apache2
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Listar todos os serviços</span><span>
</span><span>systemctl list-units </span><span class="token parameter" style="color:rgb(214, 222, 235)">--type</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span>service
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Listar todos os arquivos de unit</span><span>
</span>systemctl list-unit-files
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Listar dependências do Apache</span><span>
</span>systemctl list-dependencies apache2
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Recarregar Systemd após criar/modificar um arquivo .service</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> systemctl daemon-reload
</span></code></pre></div>

---

## 🎯 Targets (Níveis de Execução)

**Descrição:** Substituem os antigos "runlevels" do SysVinit. São grupos de units.

**Targets Comuns:**
- `multi-user.target`: Modo multiusuário (sem GUI).
- `graphical.target`: Modo gráfico (com GUI).
- `reboot.target`: Desligamento para reiniciar.
- `poweroff.target`: Desligamento para desligar.
- `rescue.target`: Modo de recuperação.
- `emergency.target`: Modo de emergência (apenas shell root).

**Exemplos:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-urnpxzk00" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ver target padrão</span><span>
</span>systemctl get-default
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Definir target padrão (ex: modo gráfico)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> systemctl set-default graphical.target
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Mudar para modo multiusuário (sem reiniciar)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> systemctl isolate multi-user.target
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Reiniciar sistema</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> systemctl </span><span class="token" style="color:rgb(130, 170, 255)">reboot</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Desligar sistema</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> systemctl poweroff
</span></code></pre></div>

---

## 📜 Logs do Systemd (journalctl)

**Descrição:** Ferramenta para visualizar e gerenciar logs do Systemd.

**Ver detalhes completos em:** [[22_Auditoria-e-Logs]]

### Exemplos

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-wagealbpo" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ver todos os logs</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> journalctl
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ver logs do boot atual</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> journalctl </span><span class="token parameter" style="color:rgb(214, 222, 235)">-b</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ver logs de um serviço específico</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> journalctl </span><span class="token parameter" style="color:rgb(214, 222, 235)">-u</span><span> apache2
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ver logs em tempo real</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> journalctl </span><span class="token parameter" style="color:rgb(214, 222, 235)">-f</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ver logs de erro</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> journalctl </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> err
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ver logs de um período</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> journalctl </span><span class="token parameter" style="color:rgb(214, 222, 235)">--since</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;2025-01-01 10:00:00&quot;</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">--until</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;2025-01-01 11:00:00&quot;</span><span>
</span></code></pre></div>

---

## 🔗 Links Relacionados

- [[13_Cron-e-Agendamento]]
- [[22_Auditoria-e-Logs]]
- [[23_Bash-Scripting]]
- [[27_Apache]]
- [[19_Hardening-Linux]]

---

## 📚 Referências

- Systemd Wikipedia: [en.wikipedia.org/wiki/Systemd](https://en.wikipedia.org/wiki/Systemd)
- Systemctl Man Page: [man7.org/linux/man-pages/man1/systemctl.1.html](https://man7.org/linux/man-pages/man1/systemctl.1.html)
- Journalctl Man Page: [man7.org/linux/man-pages/man1/journalctl.1.html](https://man7.org/linux/man-pages/man1/journalct
