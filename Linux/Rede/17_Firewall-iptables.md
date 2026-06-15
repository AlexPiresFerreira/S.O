
# 🛡️ Firewall - iptables

> **Tags:** #linux #firewall #iptables #seguranca #rede #nat #filter

---

## 📌 Visão Geral

**iptables** é a ferramenta de linha de comando para configurar o **Netfilter**, o framework de firewall do kernel Linux.

🎯 **Objetivo:** Controlar o tráfego de rede (entrada, saída, encaminhamento) para proteger o sistema.

---

## 📊 Conceitos Básicos

### Tabelas (Tables)

**Descrição:** Conjuntos de cadeias (chains) que lidam com diferentes tipos de processamento de pacotes.

| Tabela | Descrição |
|--------|-----------|
| `filter` | Padrão. Usada para **filtrar** pacotes (permitir/bloquear). |
| `nat` | Usada para **Network Address Translation** (NAT). |
| `mangle` | Usada para modificar cabeçalhos de pacotes. |
| `raw` | Usada para configurar exceções de rastreamento de conexão. |
| `security` | Usada para regras de segurança SELinux. |

---

### Cadeias (Chains)

**Descrição:** Listas de regras que os pacotes atravessam.

| Cadeia | Tabela `filter` | Tabela `nat` |
|--------|-----------------|--------------|
| `INPUT` | Pacotes **para** o próprio firewall. | - |
| `OUTPUT` | Pacotes **originados** do próprio firewall. | - |
| `FORWARD` | Pacotes que **atravessam** o firewall (roteados). | - |
| `PREROUTING` | - | Pacotes antes do roteamento. |
| `POSTROUTING` | - | Pacotes após o roteamento. |

---

### Regras (Rules)

**Descrição:** Condições e ações a serem aplicadas a um pacote.

**Ações (Targets):**
- `ACCEPT`: Permitir o pacote.
- `DROP`: Descartar o pacote **silenciosamente**.
- `REJECT`: Descartar o pacote e enviar uma mensagem de erro ao remetente.
- `LOG`: Registrar o pacote no log do sistema.
- `SNAT`: Source NAT (modificar IP de origem).
- `DNAT`: Destination NAT (modificar IP de destino).
- `MASQUERADE`: SNAT dinâmico (para IPs dinâmicos).

---

## 🚀 Sintaxe Básica

`sudo iptables -t <tabela> -[A|D] <cadeia> [critérios] -j <ação>`

- `-t <tabela>`: Especifica a tabela (padrão é `filter`).
- `-A <cadeia>`: Adiciona regra ao final da cadeia.
- `-D <cadeia>`: Deleta regra da cadeia.
- `-I <cadeia> [num]`: Insere regra no início ou em posição específica.
- `-L <cadeia>`: Lista regras da cadeia.
- `-F <cadeia>`: Limpa todas as regras da cadeia.
- `-P <cadeia> <ação>`: Define política padrão da cadeia.

---

## 💻 Comandos de Listagem

### Listar Todas as Regras

bash
#### Listar todas as regras da tabela filter (padrão)

sudo iptables -L
#### Listar todas as regras da tabela filter com números e verbose

sudo iptables -L -v -n --line-numbers
#### Listar regras de uma tabela específica (ex: nat)

sudo iptables -t nat -L -v -n

---

## 🛡️ Regras de Filtragem (Tabela `filter`)

### Políticas Padrão (Default Policies)

**Descrição:** Ação a ser tomada se nenhum regra corresponder.

**Recomendado:** Definir políticas padrão como `DROP` e permitir explicitamente o que é necessário.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-jg1yrd2w6" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Definir política padrão para DROP (entrada, encaminhamento, saída)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-P</span><span> INPUT DROP
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-P</span><span> FORWARD DROP
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-P</span><span> OUTPUT DROP
</span></code></pre></div>

**⚠️ Cuidado:** Se você definir `DROP` para `INPUT` e não tiver regras para `ACCEPT` SSH, você será desconectado!

---

### Regras de INPUT (Para o Firewall)

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-seyrzzbg6" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Permitir conexões SSH (porta 22)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-A</span><span> INPUT </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> tcp </span><span class="token parameter" style="color:rgb(214, 222, 235)">--dport</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">22</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-j</span><span> ACCEPT
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Permitir conexões SSH de um IP específico</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-A</span><span> INPUT </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> tcp </span><span class="token parameter" style="color:rgb(214, 222, 235)">-s</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">192.168</span><span>.1.10 </span><span class="token parameter" style="color:rgb(214, 222, 235)">--dport</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">22</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-j</span><span> ACCEPT
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Permitir conexões HTTP (porta 80)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-A</span><span> INPUT </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> tcp </span><span class="token parameter" style="color:rgb(214, 222, 235)">--dport</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">80</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-j</span><span> ACCEPT
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Bloquear ICMP (ping)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-A</span><span> INPUT </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> icmp </span><span class="token parameter" style="color:rgb(214, 222, 235)">-j</span><span> DROP
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Permitir tráfego na interface de loopback</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-A</span><span> INPUT </span><span class="token parameter" style="color:rgb(214, 222, 235)">-i</span><span> lo </span><span class="token parameter" style="color:rgb(214, 222, 235)">-j</span><span> ACCEPT
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Permitir conexões já estabelecidas ou relacionadas</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-A</span><span> INPUT </span><span class="token parameter" style="color:rgb(214, 222, 235)">-m</span><span> state </span><span class="token parameter" style="color:rgb(214, 222, 235)">--state</span><span> ESTABLISHED,RELATED </span><span class="token parameter" style="color:rgb(214, 222, 235)">-j</span><span> ACCEPT
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Limitar novas conexões SSH para evitar brute force</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-A</span><span> INPUT </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> tcp </span><span class="token parameter" style="color:rgb(214, 222, 235)">--dport</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">22</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-m</span><span> state </span><span class="token parameter" style="color:rgb(214, 222, 235)">--state</span><span> NEW </span><span class="token parameter" style="color:rgb(214, 222, 235)">-m</span><span> limit </span><span class="token parameter" style="color:rgb(214, 222, 235)">--limit</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">5</span><span>/minute --limit-burst </span><span class="token" style="color:rgb(247, 140, 108)">10</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-j</span><span> ACCEPT
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-A</span><span> INPUT </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> tcp </span><span class="token parameter" style="color:rgb(214, 222, 235)">--dport</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">22</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-j</span><span> DROP </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Bloqueia o excesso</span><span>
</span></code></pre></div>

---

### Regras de OUTPUT (Do Firewall)

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-7ouaykqi5" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Permitir saída de conexões SSH</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-A</span><span> OUTPUT </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> tcp </span><span class="token parameter" style="color:rgb(214, 222, 235)">--sport</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">22</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-j</span><span> ACCEPT
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Permitir saída de conexões HTTP/HTTPS</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-A</span><span> OUTPUT </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> tcp </span><span class="token parameter" style="color:rgb(214, 222, 235)">--dport</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">80</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-j</span><span> ACCEPT
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-A</span><span> OUTPUT </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> tcp </span><span class="token parameter" style="color:rgb(214, 222, 235)">--dport</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">443</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-j</span><span> ACCEPT
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Permitir saída de DNS</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-A</span><span> OUTPUT </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> udp </span><span class="token parameter" style="color:rgb(214, 222, 235)">--dport</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">53</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-j</span><span> ACCEPT
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Permitir saída de ICMP (ping)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-A</span><span> OUTPUT </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> icmp </span><span class="token parameter" style="color:rgb(214, 222, 235)">-j</span><span> ACCEPT
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Permitir conexões já estabelecidas ou relacionadas</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-A</span><span> OUTPUT </span><span class="token parameter" style="color:rgb(214, 222, 235)">-m</span><span> state </span><span class="token parameter" style="color:rgb(214, 222, 235)">--state</span><span> ESTABLISHED,RELATED </span><span class="token parameter" style="color:rgb(214, 222, 235)">-j</span><span> ACCEPT
</span></code></pre></div>

---

### Regras de FORWARD (Atravessando o Firewall)

**Uso:** Quando o Linux atua como roteador.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-ak2r418yz" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Permitir encaminhamento de uma interface para outra</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-A</span><span> FORWARD </span><span class="token parameter" style="color:rgb(214, 222, 235)">-i</span><span> eth0 </span><span class="token parameter" style="color:rgb(214, 222, 235)">-o</span><span> eth1 </span><span class="token parameter" style="color:rgb(214, 222, 235)">-j</span><span> ACCEPT
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Bloquear encaminhamento para um IP específico</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-A</span><span> FORWARD </span><span class="token parameter" style="color:rgb(214, 222, 235)">-d</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">10.0</span><span>.0.10 </span><span class="token parameter" style="color:rgb(214, 222, 235)">-j</span><span> DROP
</span></code></pre></div>

---

## 🌐 NAT (Network Address Translation - Tabela `nat`)

### SNAT (Source NAT) / Masquerade

**Descrição:** Modifica o endereço IP de origem de pacotes. Usado para permitir que máquinas em uma rede privada acessem a internet através de um único IP público.

**Requer:** Habilitar encaminhamento de IP no kernel:
`sudo sysctl -w net.ipv4.ip_forward=1`
`echo "net.ipv4.ip_forward=1" | sudo tee -a /etc/sysctl.conf`

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-e4jerl4z1" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Masquerade (para IPs dinâmicos)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-t</span><span> nat </span><span class="token parameter" style="color:rgb(214, 222, 235)">-A</span><span> POSTROUTING </span><span class="token parameter" style="color:rgb(214, 222, 235)">-o</span><span> eth0 </span><span class="token parameter" style="color:rgb(214, 222, 235)">-j</span><span> MASQUERADE
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># SNAT (para IPs estáticos)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-t</span><span> nat </span><span class="token parameter" style="color:rgb(214, 222, 235)">-A</span><span> POSTROUTING </span><span class="token parameter" style="color:rgb(214, 222, 235)">-o</span><span> eth0 </span><span class="token parameter" style="color:rgb(214, 222, 235)">-j</span><span> SNAT --to-source </span><span class="token" style="color:rgb(247, 140, 108)">203.0</span><span>.113.10
</span></code></pre></div>

---

### DNAT (Destination NAT)

**Descrição:** Modifica o endereço IP de destino de pacotes. Usado para redirecionar tráfego de uma porta pública para um servidor interno (Port Forwarding).

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-45da6cvol" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Redirecionar porta 80 pública para servidor web interno</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-t</span><span> nat </span><span class="token parameter" style="color:rgb(214, 222, 235)">-A</span><span> PREROUTING </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> tcp </span><span class="token parameter" style="color:rgb(214, 222, 235)">--dport</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">80</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-i</span><span> eth0 </span><span class="token parameter" style="color:rgb(214, 222, 235)">-j</span><span> DNAT --to-destination </span><span class="token" style="color:rgb(247, 140, 108)">192.168</span><span>.1.10:80
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Redirecionar porta 2222 pública para SSH interno</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-t</span><span> nat </span><span class="token parameter" style="color:rgb(214, 222, 235)">-A</span><span> PREROUTING </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> tcp </span><span class="token parameter" style="color:rgb(214, 222, 235)">--dport</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">2222</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-i</span><span> eth0 </span><span class="token parameter" style="color:rgb(214, 222, 235)">-j</span><span> DNAT --to-destination </span><span class="token" style="color:rgb(247, 140, 108)">192.168</span><span>.1.20:22
</span></code></pre></div>

---

## 📝 Outras Ações

### LOG

**Descrição:** Registra informações sobre pacotes que correspondem à regra.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-oxeqix3u5" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Logar pacotes ICMP</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-A</span><span> INPUT </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> icmp </span><span class="token parameter" style="color:rgb(214, 222, 235)">-j</span><span> LOG --log-prefix </span><span class="token" style="color:rgb(173, 219, 103)">&quot;IPTABLES_ICMP: &quot;</span><span>
</span></code></pre></div>

---

### REJECT

**Descrição:** Rejeita o pacote e envia uma mensagem de erro (ex: ICMP Port Unreachable).

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-boc30l8d7" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Rejeitar conexões para porta 23 (Telnet)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-A</span><span> INPUT </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> tcp </span><span class="token parameter" style="color:rgb(214, 222, 235)">--dport</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">23</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-j</span><span> REJECT
</span></code></pre></div>

---

## 🗑️ Gerenciamento de Regras

### Limpar Todas as Regras

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-cpp26602r" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Limpar todas as regras de todas as cadeias na tabela filter</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-F</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Limpar todas as regras de todas as cadeias na tabela nat</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-t</span><span> nat </span><span class="token parameter" style="color:rgb(214, 222, 235)">-F</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Limpar todas as regras de todas as tabelas</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-F</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-t</span><span> nat </span><span class="token parameter" style="color:rgb(214, 222, 235)">-F</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-t</span><span> mangle </span><span class="token parameter" style="color:rgb(214, 222, 235)">-F</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-t</span><span> raw </span><span class="token parameter" style="color:rgb(214, 222, 235)">-F</span><span>
</span></code></pre></div>

---

### Deletar Regra Específica

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-akj0oibe0" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Deletar regra pelo número da linha</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-D</span><span> INPUT </span><span class="token" style="color:rgb(247, 140, 108)">5</span><span>  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Deleta a 5ª regra da cadeia INPUT</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Deletar regra pela especificação</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-D</span><span> INPUT </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> tcp </span><span class="token parameter" style="color:rgb(214, 222, 235)">--dport</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">22</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-j</span><span> ACCEPT
</span></code></pre></div>

---

### Resetar Políticas Padrão

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-cxp4dr8r3" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Resetar políticas para ACCEPT</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-P</span><span> INPUT ACCEPT
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-P</span><span> FORWARD ACCEPT
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-P</span><span> OUTPUT ACCEPT
</span></code></pre></div>

---

## 💾 Persistência das Regras

**Descrição:** As regras do `iptables` são voláteis e são perdidas no reboot.

### Debian/Ubuntu

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-t7pl38l47" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Instalar pacote para salvar regras</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">apt</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">install</span><span> iptables-persistent
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Salvar regras atuais</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> netfilter-persistent save
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># As regras são salvas em:</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># /etc/iptables/rules.v4 (IPv4)</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># /etc/iptables/rules.v6 (IPv6)</span><span>
</span></code></pre></div>

---

### Red Hat/CentOS

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-wewysxdsl" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Salvar regras atuais</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables-save </span><span class="token" style="color:rgb(127, 219, 202)">&gt;</span><span> /etc/sysconfig/iptables
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Restaurar regras no boot (habilitar serviço)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> systemctl </span><span class="token" style="color:rgb(255, 203, 139)">enable</span><span> iptables
</span></code></pre></div>

---

## 🆕 nftables (Substituto Moderno)

**Descrição:** O `nftables` é o framework de firewall de próxima geração, projetado para substituir o `iptables`.

**Vantagens:**
- Sintaxe mais simples e unificada.
- Melhor desempenho.
- Suporte a IPv4 e IPv6 em um único conjunto de regras.

**Uso:** `sudo nft list ruleset`

---

## 🔗 Links Relacionados

- [[14_Configuracao-de-Rede]]
- [[15_Ferramentas-de-Rede]]
- [[18_Monitoramento-de-Rede]]
- [[19_Hardening-Linux]]

---

## 📚 Referências

- Iptables Man Page: [man7.org/linux/man-pages/man8/iptables.8.html](https://man7.org/linux/man-pages/man8/iptables.8.html)
- Netfilter: [www.netfilter.org](https://www.netfilter.org/)
- Nftables: [wiki.nftables.org](https://wiki.nftables.org/)
- Iptables Tutorial: [www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-with-iptables-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-with-iptables-on-ubuntu-16-04)