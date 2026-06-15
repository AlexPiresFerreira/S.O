
# 🤖 Automação com Shell Script no Linux

> **Tags:** #linux #automacao #shell-script #administracao #seguranca #cron #systemd

---

## 📌 Visão Geral

A automação de tarefas repetitivas é um pilar da administração de sistemas e segurança, economizando tempo e reduzindo erros.

🎯 **Objetivo:** Criar scripts para automatizar tarefas comuns e agendá-las para execução periódica.

---

## 🚀 Por que Automatizar?

- **Eficiência:** Executar tarefas rapidamente.
- **Consistência:** Reduzir erros humanos.
- **Escalabilidade:** Gerenciar múltiplos sistemas.
- **Segurança:** Automatizar verificações e hardening.
- **Monitoramento:** Gerar relatórios e alertas.

---

## 📝 Elementos Chave para Automação

### 1. Shell Scripting

**Descrição:** A base da automação no Linux.

**Ver detalhes em:** [[23_Bash-Scripting]]

---

### 2. Agendamento de Tarefas

**Descrição:** Executar scripts automaticamente em horários definidos.

**Ver detalhes em:** [[13_Cron-e-Agendamento]]

---

### 3. Redirecionamento e Pipes

**Descrição:** Conectar a saída de um comando à entrada de outro, e direcionar saídas para arquivos.

**Ver detalhes em:** [[04_Gerenciamento-de-Arquivos]]

---

### 4. Expressões Regulares

**Descrição:** Filtrar e extrair informações de texto (logs, configurações).

**Ver detalhes em:** [[25_Expressoes-Regulares]]

---

## 💻 Exemplos de Scripts de Automação

### Script 1: Backup Simples de Diretório

**Nome:** `backup_home.sh`

bash
#### !/bin/bash

#### Script para fazer backup do diretório home

DATA=$(date +%Y%m%d_%H%M%S) BACKUP_DIR="/var/backups/home" ORIGEM="/home/usuario" ARQUIVO_BACKUP="$BACKUP_DIR/home_backup_$DATA.tar.gz" LOG_FILE="/var/log/backup_home.log"

# Criar diretório de backup se não existir

mkdir -p "$BACKUP_DIR"

echo "--- Iniciando backup em $DATA ---" >> "$LOG_FILE"

#### Criar o backup

tar -czf "$ARQUIVO_BACKUP" "$ORIGEM" 2>> "$LOG_FILE"

if [ $? -eq 0 ]; then echo "Backup de $ORIGEM concluído com sucesso em $ARQUIVO_BACKUP" >> "$LOG_FILE" # Remover backups antigos (manter os últimos 7 dias) find "$BACKUP_DIR" -type f -name "home_backup_*.tar.gz" -mtime +7 -delete echo "Backups antigos removidos." >> "$LOG_FILE" else echo "ERRO: Falha no backup de $ORIGEM" >> "$LOG_FILE" fi

echo "--- Backup finalizado ---" >> "$LOG_FILE"

```
**Agendamento (Crontab - diário à 01:00):**

0 1 * * * /caminho/do/backup_home.sh

```

---

### Script 2: Verificação de Portas Abertas

**Nome:** `check_open_ports.sh`

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-4vc9vgvwp" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token shebang" style="color:rgb(214, 222, 235);font-weight:bold">#!/bin/bash</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Script para verificar portas abertas e alertar sobre novas</span><span>
</span>
<span></span><span class="token assign-left" style="color:rgb(214, 222, 235)">LOG_FILE</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span class="token" style="color:rgb(173, 219, 103)">&quot;/var/log/open_ports.log&quot;</span><span>
</span><span></span><span class="token assign-left" style="color:rgb(214, 222, 235)">CURRENT_PORTS_FILE</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span class="token" style="color:rgb(173, 219, 103)">&quot;/tmp/current_open_ports.txt&quot;</span><span>
</span><span></span><span class="token assign-left" style="color:rgb(214, 222, 235)">PREVIOUS_PORTS_FILE</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span class="token" style="color:rgb(173, 219, 103)">&quot;/tmp/previous_open_ports.txt&quot;</span><span>
</span><span></span><span class="token assign-left" style="color:rgb(214, 222, 235)">ALERT_EMAIL</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span class="token" style="color:rgb(173, 219, 103)">&quot;alex@exemplo.com&quot;</span><span>
</span>
<span></span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;--- Verificação de portas abertas em </span><span class="token" style="color:rgb(214, 222, 235)">$(</span><span class="token" style="color:rgb(130, 170, 255)">date</span><span class="token" style="color:rgb(214, 222, 235)">)</span><span class="token" style="color:rgb(173, 219, 103)"> ---&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">&gt;&gt;</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span class="token" style="color:rgb(214, 222, 235)">$LOG_FILE</span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Obter portas TCP em LISTEN</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> ss </span><span class="token parameter" style="color:rgb(214, 222, 235)">-tlnp</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">awk</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;NR&gt;1 {print $4}&#x27;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">cut</span><span> -d: </span><span class="token parameter" style="color:rgb(214, 222, 235)">-f2</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">sort</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-n</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">&gt;</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span class="token" style="color:rgb(214, 222, 235)">$CURRENT_PORTS_FILE</span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Comparar com o estado anterior</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">if</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">[</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-f</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span class="token" style="color:rgb(214, 222, 235)">$PREVIOUS_PORTS_FILE</span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">]</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">then</span><span>
</span><span>    </span><span class="token assign-left" style="color:rgb(214, 222, 235)">NEW_PORTS</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span class="token" style="color:rgb(214, 222, 235)">$(</span><span class="token" style="color:rgb(130, 170, 255)">comm</span><span class="token" style="color:rgb(214, 222, 235)"> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-13</span><span class="token" style="color:rgb(214, 222, 235)"> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span class="token" style="color:rgb(173, 219, 103)">$PREVIOUS_PORTS_FILE</span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span class="token" style="color:rgb(214, 222, 235)"> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span class="token" style="color:rgb(173, 219, 103)">$CURRENT_PORTS_FILE</span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span class="token" style="color:rgb(214, 222, 235)">)</span><span>
</span><span>    </span><span class="token assign-left" style="color:rgb(214, 222, 235)">CLOSED_PORTS</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span class="token" style="color:rgb(214, 222, 235)">$(</span><span class="token" style="color:rgb(130, 170, 255)">comm</span><span class="token" style="color:rgb(214, 222, 235)"> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-23</span><span class="token" style="color:rgb(214, 222, 235)"> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span class="token" style="color:rgb(173, 219, 103)">$PREVIOUS_PORTS_FILE</span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span class="token" style="color:rgb(214, 222, 235)"> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span class="token" style="color:rgb(173, 219, 103)">$CURRENT_PORTS_FILE</span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span class="token" style="color:rgb(214, 222, 235)">)</span><span>
</span>
<span>    </span><span class="token" style="color:rgb(127, 219, 202)">if</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">[</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-n</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span class="token" style="color:rgb(214, 222, 235)">$NEW_PORTS</span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">]</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">then</span><span>
</span><span>        </span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;ALERTA: Novas portas abertas detectadas!&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">tee</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-a</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span class="token" style="color:rgb(214, 222, 235)">$LOG_FILE</span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span>
</span><span>        </span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span class="token" style="color:rgb(214, 222, 235)">$NEW_PORTS</span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">tee</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-a</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span class="token" style="color:rgb(214, 222, 235)">$LOG_FILE</span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span>
</span><span>        </span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Novas portas abertas: </span><span class="token" style="color:rgb(214, 222, 235)">$NEW_PORTS</span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> mail </span><span class="token parameter" style="color:rgb(214, 222, 235)">-s</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;ALERTA: Novas portas abertas&quot;</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span class="token" style="color:rgb(214, 222, 235)">$ALERT_EMAIL</span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span>
</span><span>    </span><span class="token" style="color:rgb(127, 219, 202)">fi</span><span>
</span>
<span>    </span><span class="token" style="color:rgb(127, 219, 202)">if</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">[</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-n</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span class="token" style="color:rgb(214, 222, 235)">$CLOSED_PORTS</span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">]</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">then</span><span>
</span><span>        </span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Portas fechadas: </span><span class="token" style="color:rgb(214, 222, 235)">$CLOSED_PORTS</span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">tee</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-a</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span class="token" style="color:rgb(214, 222, 235)">$LOG_FILE</span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span>
</span><span>    </span><span class="token" style="color:rgb(127, 219, 202)">fi</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">else</span><span>
</span><span>    </span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Primeira execução. Salvando estado atual das portas.&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">&gt;&gt;</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span class="token" style="color:rgb(214, 222, 235)">$LOG_FILE</span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">fi</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Atualizar estado anterior</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">mv</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span class="token" style="color:rgb(214, 222, 235)">$CURRENT_PORTS_FILE</span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span class="token" style="color:rgb(214, 222, 235)">$PREVIOUS_PORTS_FILE</span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span>
</span>
<span></span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;--- Verificação concluída ---&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">&gt;&gt;</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span class="token" style="color:rgb(214, 222, 235)">$LOG_FILE</span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span>
</span></code></pre></div>

**Agendamento (Crontab - a cada 30 minutos):**
```

_/30_ * * * /caminho/do/check_open_ports.sh

```
---

### Script 3: Monitoramento de Uso de Disco

**Nome:** `monitor_disk_usage.sh`

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-vqod4xn3o" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token shebang" style="color:rgb(214, 222, 235);font-weight:bold">#!/bin/bash</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Script para monitorar uso de disco e alertar se exceder limite</span><span>
</span>
<span></span><span class="token assign-left" style="color:rgb(214, 222, 235)">THRESHOLD</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span class="token" style="color:rgb(247, 140, 108)">80</span><span> </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Limite de uso em %</span><span>
</span><span></span><span class="token assign-left" style="color:rgb(214, 222, 235)">ALERT_EMAIL</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span class="token" style="color:rgb(173, 219, 103)">&quot;alex@exemplo.com&quot;</span><span>
</span><span></span><span class="token assign-left" style="color:rgb(214, 222, 235)">LOG_FILE</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span class="token" style="color:rgb(173, 219, 103)">&quot;/var/log/disk_usage_monitor.log&quot;</span><span>
</span>
<span></span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;--- Monitoramento de disco em </span><span class="token" style="color:rgb(214, 222, 235)">$(</span><span class="token" style="color:rgb(130, 170, 255)">date</span><span class="token" style="color:rgb(214, 222, 235)">)</span><span class="token" style="color:rgb(173, 219, 103)"> ---&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">&gt;&gt;</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span class="token" style="color:rgb(214, 222, 235)">$LOG_FILE</span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Obter uso de disco das partições</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">df</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-h</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">grep</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-vE</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;^Filesystem|tmpfs|cdrom&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">awk</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;{print $5 &quot; &quot; $1}&#x27;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">while</span><span> </span><span class="token" style="color:rgb(255, 203, 139)">read</span><span> OUTPUT</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">do</span><span>
</span><span>    </span><span class="token assign-left" style="color:rgb(214, 222, 235)">USE_PERCENT</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span class="token" style="color:rgb(214, 222, 235)">$(</span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span class="token" style="color:rgb(214, 222, 235)"> $OUTPUT </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span class="token" style="color:rgb(214, 222, 235)"> </span><span class="token" style="color:rgb(130, 170, 255)">awk</span><span class="token" style="color:rgb(214, 222, 235)"> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;{print $1}&#x27;</span><span class="token" style="color:rgb(214, 222, 235)"> </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span class="token" style="color:rgb(214, 222, 235)"> </span><span class="token" style="color:rgb(130, 170, 255)">sed</span><span class="token" style="color:rgb(214, 222, 235)"> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;s/%//g&#x27;</span><span class="token" style="color:rgb(214, 222, 235)">)</span><span>
</span><span>    </span><span class="token assign-left" style="color:rgb(214, 222, 235)">PARTITION</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span class="token" style="color:rgb(214, 222, 235)">$(</span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span class="token" style="color:rgb(214, 222, 235)"> $OUTPUT </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span class="token" style="color:rgb(214, 222, 235)"> </span><span class="token" style="color:rgb(130, 170, 255)">awk</span><span class="token" style="color:rgb(214, 222, 235)"> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;{print $2}&#x27;</span><span class="token" style="color:rgb(214, 222, 235)">)</span><span>
</span>
<span>    </span><span class="token" style="color:rgb(127, 219, 202)">if</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">[</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span class="token" style="color:rgb(214, 222, 235)">$USE_PERCENT</span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-ge</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span class="token" style="color:rgb(214, 222, 235)">$THRESHOLD</span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">]</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">then</span><span>
</span><span>        </span><span class="token assign-left" style="color:rgb(214, 222, 235)">MESSAGE</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span class="token" style="color:rgb(173, 219, 103)">&quot;ALERTA: Uso de disco da partição </span><span class="token" style="color:rgb(214, 222, 235)">$PARTITION</span><span class="token" style="color:rgb(173, 219, 103)"> está em </span><span class="token" style="color:rgb(214, 222, 235)">$USE_PERCENT</span><span class="token" style="color:rgb(173, 219, 103)">% (limite: </span><span class="token" style="color:rgb(214, 222, 235)">$THRESHOLD</span><span class="token" style="color:rgb(173, 219, 103)">%)&quot;</span><span>
</span><span>        </span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span class="token" style="color:rgb(214, 222, 235)">$MESSAGE</span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">tee</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-a</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span class="token" style="color:rgb(214, 222, 235)">$LOG_FILE</span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span>
</span><span>        </span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span class="token" style="color:rgb(214, 222, 235)">$MESSAGE</span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> mail </span><span class="token parameter" style="color:rgb(214, 222, 235)">-s</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;ALERTA: Uso de disco alto&quot;</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span class="token" style="color:rgb(214, 222, 235)">$ALERT_EMAIL</span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span>
</span><span>    </span><span class="token" style="color:rgb(127, 219, 202)">else</span><span>
</span><span>        </span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Partição </span><span class="token" style="color:rgb(214, 222, 235)">$PARTITION</span><span class="token" style="color:rgb(173, 219, 103)">: </span><span class="token" style="color:rgb(214, 222, 235)">$USE_PERCENT</span><span class="token" style="color:rgb(173, 219, 103)">% de uso (OK)&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">&gt;&gt;</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span class="token" style="color:rgb(214, 222, 235)">$LOG_FILE</span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span>
</span><span>    </span><span class="token" style="color:rgb(127, 219, 202)">fi</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">done</span><span>
</span>
<span></span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;--- Monitoramento concluído ---&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">&gt;&gt;</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span class="token" style="color:rgb(214, 222, 235)">$LOG_FILE</span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span>
</span></code></pre></div>

**Agendamento (Crontab - a cada 4 horas):**
```

0 _/4_ * * /caminho/do/monitor_disk_usage.sh

```
---

## ⚠️ Boas Práticas para Scripts de Automação

- **Caminhos absolutos:** Sempre use caminhos completos para comandos e arquivos.
- **Logs:** Redirecione a saída para arquivos de log e erros para facilitar o troubleshooting.
- **Permissões:** Garanta que o script tenha permissão de execução (`chmod +x`).
- **Variáveis:** Use variáveis para valores configuráveis (limites, e-mails).
- **Testes:** Teste o script manualmente antes de agendá-lo.
- **Idempotência:** Idealmente, o script deve produzir o mesmo resultado se executado múltiplas vezes.
- **Notificações:** Configure alertas por e-mail ou outros meios para eventos críticos.
- **Segurança:** Evite senhas hardcoded, use chaves SSH ou outras formas seguras de credenciais.

---

## 🔗 Links Relacionados

- [[23_Bash-Scripting]]
- [[13_Cron-e-Agendamento]]
- [[25_Expressoes-Regulares]]
- [[24_AWK-Avancado]]
- [[22_Auditoria-e-Logs]]

---

## 📚 Referências

- Linux Automation: [www.redhat.com/en/topics/automation](https://www.redhat.com/en/topics/automation)
- Bash Scripting Tutorial: [ryanstutorials.net/bash-scripting-tutorial](https://ryanstutorials.net/bash-scripting-tutorial)
