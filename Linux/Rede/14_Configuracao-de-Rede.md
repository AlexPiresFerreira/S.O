
# 🌐 Configuração de Rede no Linux

> **Tags:** #linux #rede #network #ip #ifconfig #nmcli #netplan #dns #gateway

---

## 📌 Visão Geral

Configurar a rede é uma das tarefas mais importantes na administração de sistemas Linux, seja para servidores ou desktops.

🎯 **Objetivo:** Entender e aplicar configurações de rede IP, DNS e roteamento.

---

## 📊 Conceitos Básicos

### Endereço IP

**Descrição:** Identificador numérico de um dispositivo na rede.

- **IPv4:** `192.168.1.10`
- **IPv6:** `fe80::a00:27ff:fede:c7af`

---

### Máscara de Sub-rede (Netmask)

**Descrição:** Define a porção de rede e a porção de host de um endereço IP.

- **IPv4:** `255.255.255.0` ou `/24`
- **IPv6:** `/64`

---

### Gateway Padrão (Default Gateway)

**Descrição:** O endereço IP do roteador que encaminha o tráfego para outras redes (incluindo a internet).

---

### Servidor DNS (Domain Name System)

**Descrição:** Traduz nomes de domínio (ex: `google.com`) para endereços IP.

---

### Interface de Rede

**Descrição:** Placa de rede física ou virtual (ex: `eth0`, `enp0s3`, `wlan0`).

---

## 🛠️ Ferramentas de Configuração

### 1️⃣ ifconfig (Legacy)

**Descrição:** Ferramenta tradicional para configurar interfaces de rede.

**Instalação (se não vier pré-instalado):**

bash sudo apt install net-tools # Debian/Ubuntu

**Exemplos:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-e0g33vqgq" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Exibir todas as interfaces</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">ifconfig</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Exibir interface específica</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">ifconfig</span><span> eth0
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ativar interface</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">ifconfig</span><span> eth0 up
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Desativar interface</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">ifconfig</span><span> eth0 down
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Atribuir IP e máscara</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">ifconfig</span><span> eth0 </span><span class="token" style="color:rgb(247, 140, 108)">192.168</span><span>.1.10 netmask </span><span class="token" style="color:rgb(247, 140, 108)">255.255</span><span>.255.0
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Adicionar IP (sem remover o anterior)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">ifconfig</span><span> eth0:0 </span><span class="token" style="color:rgb(247, 140, 108)">192.168</span><span>.1.11 netmask </span><span class="token" style="color:rgb(247, 140, 108)">255.255</span><span>.255.0
</span></code></pre></div>

---

### 2️⃣ ip (Moderno)

**Descrição:** Ferramenta moderna e mais poderosa para configurar interfaces de rede e roteamento.

**Sintaxe:** `ip [opções] [objeto] [comando]`

**Objetos:**
- `link`: Interfaces de rede (físicas e virtuais).
- `address` ou `addr`: Endereços IP.
- `route`: Tabela de roteamento.
- `neigh`: Tabela ARP (vizinhos).

**Exemplos:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-yblyjmtd4" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Exibir todas as interfaces (ip link show)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">ip</span><span> a
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Exibir interface específica</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">ip</span><span> a show enp0s3
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ativar interface</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">ip</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">link</span><span> </span><span class="token" style="color:rgb(255, 203, 139)">set</span><span> enp0s3 up
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Desativar interface</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">ip</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">link</span><span> </span><span class="token" style="color:rgb(255, 203, 139)">set</span><span> enp0s3 down
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Adicionar IP e máscara</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">ip</span><span> addr </span><span class="token" style="color:rgb(130, 170, 255)">add</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">192.168</span><span>.1.10/24 dev enp0s3
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Deletar IP</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">ip</span><span> addr del </span><span class="token" style="color:rgb(247, 140, 108)">192.168</span><span>.1.10/24 dev enp0s3
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Exibir tabela de roteamento</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">ip</span><span> r
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Adicionar rota padrão (gateway)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">ip</span><span> route </span><span class="token" style="color:rgb(130, 170, 255)">add</span><span> default via </span><span class="token" style="color:rgb(247, 140, 108)">192.168</span><span>.1.1 dev enp0s3
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Deletar rota padrão</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">ip</span><span> route del default via </span><span class="token" style="color:rgb(247, 140, 108)">192.168</span><span>.1.1 dev enp0s3
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Exibir tabela ARP</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">ip</span><span> neigh
</span></code></pre></div>

---

### 3️⃣ nmcli (NetworkManager CLI)

**Descrição:** Interface de linha de comando para o NetworkManager (usado em desktops e alguns servidores).

**Sintaxe:** `nmcli [opções] [objeto] [comando]`

**Objetos:**
- `device` ou `dev`: Dispositivos de rede.
- `connection` ou `con`: Conexões de rede.

**Exemplos:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-7cvahtdqz" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Exibir status dos dispositivos</span><span>
</span>nmcli dev status
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Exibir conexões ativas</span><span>
</span><span>nmcli con show </span><span class="token parameter" style="color:rgb(214, 222, 235)">--active</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Exibir todas as conexões</span><span>
</span>nmcli con show
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Exibir detalhes de uma conexão</span><span>
</span><span>nmcli con show </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Wired connection 1&quot;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Criar nova conexão Ethernet (DHCP)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> nmcli con </span><span class="token" style="color:rgb(130, 170, 255)">add</span><span> con-name </span><span class="token" style="color:rgb(173, 219, 103)">&quot;MinhaConexao&quot;</span><span> </span><span class="token" style="color:rgb(255, 203, 139)">type</span><span> ethernet ifname enp0s3
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Criar nova conexão Ethernet (IP estático)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> nmcli con </span><span class="token" style="color:rgb(130, 170, 255)">add</span><span> con-name </span><span class="token" style="color:rgb(173, 219, 103)">&quot;StaticEth&quot;</span><span> </span><span class="token" style="color:rgb(255, 203, 139)">type</span><span> ethernet ifname enp0s3 </span><span class="token" style="color:rgb(199, 146, 234)">\</span><span>
</span><span>  ip4 </span><span class="token" style="color:rgb(247, 140, 108)">192.168</span><span>.1.20/24 gw4 </span><span class="token" style="color:rgb(247, 140, 108)">192.168</span><span>.1.1 </span><span class="token" style="color:rgb(199, 146, 234)">\</span><span>
</span><span>  dns </span><span class="token" style="color:rgb(173, 219, 103)">&quot;8.8.8.8,8.8.4.4&quot;</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">\</span><span>
</span>  autoconnect no
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ativar conexão</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> nmcli con up </span><span class="token" style="color:rgb(173, 219, 103)">&quot;StaticEth&quot;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Desativar conexão</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> nmcli con down </span><span class="token" style="color:rgb(173, 219, 103)">&quot;StaticEth&quot;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Modificar IP de uma conexão</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> nmcli con modify </span><span class="token" style="color:rgb(173, 219, 103)">&quot;StaticEth&quot;</span><span> ipv4.addresses </span><span class="token" style="color:rgb(173, 219, 103)">&quot;192.168.1.21/24&quot;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Modificar DNS</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> nmcli con modify </span><span class="token" style="color:rgb(173, 219, 103)">&quot;StaticEth&quot;</span><span> ipv4.dns </span><span class="token" style="color:rgb(173, 219, 103)">&quot;1.1.1.1&quot;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Excluir conexão</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> nmcli con delete </span><span class="token" style="color:rgb(173, 219, 103)">&quot;MinhaConexao&quot;</span><span>
</span></code></pre></div>

---

### 4️⃣ nmtui (NetworkManager TUI)

**Descrição:** Interface de texto interativa para o NetworkManager.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-3fdnbczeh" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> nmtui
</span></code></pre></div>

---

### 5️⃣ netplan (Moderno - Ubuntu Server)

**Descrição:** Ferramenta moderna para configurar rede no Ubuntu Server (usa arquivos YAML).

**Arquivos de configuração:** `/etc/netplan/*.yaml`

**Exemplo de arquivo YAML (DHCP):**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">yaml</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-c0yoyxiby" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-yaml" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># /etc/netplan/01-netcfg.yaml</span><span>
</span><span></span><span class="token key" style="color:rgb(255, 203, 139)">network</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>  </span><span class="token key" style="color:rgb(255, 203, 139)">version</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">2</span><span>
</span><span>  </span><span class="token key" style="color:rgb(255, 203, 139)">renderer</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> networkd
</span><span>  </span><span class="token key" style="color:rgb(255, 203, 139)">ethernets</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>    </span><span class="token key" style="color:rgb(255, 203, 139)">enp0s3</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>      </span><span class="token key" style="color:rgb(255, 203, 139)">dhcp4</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> yes
</span></code></pre></div>

**Exemplo de arquivo YAML (IP Estático):**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">yaml</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-p2n6f42qb" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-yaml" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># /etc/netplan/01-netcfg.yaml</span><span>
</span><span></span><span class="token key" style="color:rgb(255, 203, 139)">network</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>  </span><span class="token key" style="color:rgb(255, 203, 139)">version</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">2</span><span>
</span><span>  </span><span class="token key" style="color:rgb(255, 203, 139)">renderer</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> networkd
</span><span>  </span><span class="token key" style="color:rgb(255, 203, 139)">ethernets</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>    </span><span class="token key" style="color:rgb(255, 203, 139)">enp0s3</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>      </span><span class="token key" style="color:rgb(255, 203, 139)">dhcp4</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> no
</span><span>      </span><span class="token key" style="color:rgb(255, 203, 139)">addresses</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">[</span><span>192.168.1.32/24</span><span class="token" style="color:rgb(199, 146, 234)">]</span><span>
</span><span>      </span><span class="token key" style="color:rgb(255, 203, 139)">gateway4</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> 192.168.1.1
</span><span>      </span><span class="token key" style="color:rgb(255, 203, 139)">nameservers</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>        </span><span class="token key" style="color:rgb(255, 203, 139)">addresses</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">[</span><span>8.8.8.8</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>208.67.222.222</span><span class="token" style="color:rgb(199, 146, 234)">]</span><span>
</span></code></pre></div>

**Aplicar configurações:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-rqc5xcc9m" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> netplan apply
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Gerar configuração (sem aplicar)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> netplan generate
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Testar configuração (sem aplicar)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> netplan try
</span></code></pre></div>

---

## 📝 Configuração de DNS

### /etc/resolv.conf

**Descrição:** Arquivo que lista os servidores DNS a serem usados.

**Exemplo:**
```

nameserver 8.8.8.8 nameserver 8.8.4.4 search exemplo.com

```
**⚠️ Em sistemas com NetworkManager ou Systemd-resolved, este arquivo pode ser sobrescrito.**

---

### /etc/hosts

**Descrição:** Arquivo para resolução de nomes local (mapeia IPs para nomes).

**Formato:** `IP_Address FQDN Alias`

**Exemplo:**
```

127.0.0.1 localhost 192.168.1.10 meuservidor.local meuservidor

```
---

## 🛣️ Configuração de Roteamento

### route -n (Legacy)

**Descrição:** Exibe e manipula a tabela de roteamento.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-64y9fzdfo" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span>route </span><span class="token parameter" style="color:rgb(214, 222, 235)">-n</span><span>
</span></code></pre></div>

---

### ip route (Moderno)

**Descrição:** Exibe e manipula a tabela de roteamento.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-ifdo60071" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">ip</span><span> r
</span></code></pre></div>

**Exemplos:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-d06d4zmw7" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Adicionar rota padrão (gateway)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">ip</span><span> route </span><span class="token" style="color:rgb(130, 170, 255)">add</span><span> default via </span><span class="token" style="color:rgb(247, 140, 108)">192.168</span><span>.1.1 dev enp0s3
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Deletar rota padrão</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">ip</span><span> route del default via </span><span class="token" style="color:rgb(247, 140, 108)">192.168</span><span>.1.1 dev enp0s3
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Adicionar rota para uma rede específica</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">ip</span><span> route </span><span class="token" style="color:rgb(130, 170, 255)">add</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">10.0</span><span>.0.0/8 via </span><span class="token" style="color:rgb(247, 140, 108)">192.168</span><span>.1.2 dev enp0s3
</span></code></pre></div>

---

## ⚙️ Configurações Persistentes

### Debian/Ubuntu (Netplan)

- Usar arquivos `.yaml` em `/etc/netplan/`.

### Red Hat/CentOS (NetworkManager)

- Usar `nmcli` ou `nmtui`.
- Arquivos de configuração em `/etc/sysconfig/network-scripts/ifcfg-<interface>`.

---

## 🔗 Links Relacionados

- [[15_Ferramentas-de-Rede]]
- [[16_SSH]]
- [[17_Firewall-iptables]]
- [[18_Monitoramento-de-Rede]]

---

## 📚 Referências

- IP Command: [man7.org/linux/man-pages/man8/ip.8.html](https://man7.org/linux/man-pages/man-pages/man8/ip.8.html)
- Netplan: [netplan.io](https://netplan.io/)
- NetworkManager: [wiki.gnome.org/Projects/NetworkManager](https://wiki.gnome.org/Projects/NetworkManager)
- Ifconfig Man Page: [man7.org/linux/man-pages/man8/ifconfig.8.html](https://man7.org/linux/man-pages/man8/ifconfig.8.html)
