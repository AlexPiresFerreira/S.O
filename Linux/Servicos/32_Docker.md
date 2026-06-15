
# 🐳 Docker - Containerização no Linux

> **Tags:** #linux #docker #containers #containerizacao #devops #servicos #microservices

---

## 📌 Visão Geral

**Docker** é uma plataforma de containerização que permite empacotar aplicações e suas dependências em **containers** isolados e portáteis.

🎯 **Objetivo:** Simplificar o desenvolvimento, deploy e execução de aplicações, garantindo consistência entre ambientes.

---

## 🆚 Containers vs Máquinas Virtuais

| Característica | Containers (Docker) | Máquinas Virtuais (VMs) |
|----------------|---------------------|-------------------------|
| **Tamanho** | MBs | GBs |
| **Inicialização** | Segundos | Minutos |
| **Performance** | Quase nativa | Overhead do hypervisor |
| **Isolamento** | Nível de processo (compartilha kernel do host) | Nível de hardware virtualizado (cada um tem seu OS) |
| **Portabilidade** | Alta | Média |
| **Densidade** | Centenas por host | Dezenas por host |
| **Recursos** | Mais leves, mais eficientes | Mais pesadas, mais recursos |

---

## 📥 Instalação

### Linux (Debian/Ubuntu)

bash
#### Atualizar repositórios

sudo apt update
#### Instalar dependências

sudo apt install apt-transport-https ca-certificates curl software-properties-common -y
#### Adicionar chave GPG do Docker

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
#### Adicionar repositório Docker

echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
#### Instalar Docker Engine, CLI e Containerd

sudo apt update sudo apt install docker-ce docker-ce-cli containerd.io -y
#### Verificar instalação

docker --version sudo systemctl status docker
#### Adicionar usuário ao grupo docker (evitar 'sudo' para comandos docker)

sudo usermod -aG docker $USER
#### Reinicie a sessão ou faça logout/login para a mudança ter efeito


---

## 🚀 Comandos Básicos

### Imagens (docker images)

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-9ymxiyw0d" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Buscar imagem no Docker Hub</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> search nginx
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Baixar imagem</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> pull nginx
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Listar imagens locais</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> images
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Remover imagem</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> rmi nginx
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Remover imagens não utilizadas</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> image prune
</span></code></pre></div>

---

### Containers (docker run / ps / stop / rm)

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-a250ofsj5" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Executar container (modo interativo, shell)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> run </span><span class="token parameter" style="color:rgb(214, 222, 235)">-it</span><span> ubuntu /bin/bash
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Executar container (modo daemon/background)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> run </span><span class="token parameter" style="color:rgb(214, 222, 235)">-d</span><span> nginx
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Executar com nome customizado</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> run </span><span class="token parameter" style="color:rgb(214, 222, 235)">-d</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">--name</span><span> meu-nginx nginx
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Executar com mapeamento de porta (Host:8080 -&gt; Container:80)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> run </span><span class="token parameter" style="color:rgb(214, 222, 235)">-d</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">8080</span><span>:80 nginx
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Listar containers em execução</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">ps</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Listar todos os containers (incluindo parados)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">ps</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-a</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Parar container</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> stop meu-nginx
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Iniciar container parado</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> start meu-nginx
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Reiniciar container</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> restart meu-nginx
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Remover container</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">rm</span><span> meu-nginx
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Remover container forçadamente</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">rm</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-f</span><span> meu-nginx
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Remover todos os containers parados</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> container prune
</span></code></pre></div>

---

### Logs e Inspeção

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-du7dx1y97" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ver logs do container</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> logs meu-nginx
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ver logs em tempo real (follow)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> logs </span><span class="token parameter" style="color:rgb(214, 222, 235)">-f</span><span> meu-nginx
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Inspecionar container (detalhes JSON)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> inspect meu-nginx
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ver processos do container</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">top</span><span> meu-nginx
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ver estatísticas de uso (CPU, RAM, Rede)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> stats
</span></code></pre></div>

---

### Executar Comandos em Container

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-y1wowvljq" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Executar comando em container em execução</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> </span><span class="token" style="color:rgb(255, 203, 139)">exec</span><span> meu-nginx </span><span class="token" style="color:rgb(130, 170, 255)">ls</span><span> /etc
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Abrir shell interativo em container em execução</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> </span><span class="token" style="color:rgb(255, 203, 139)">exec</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-it</span><span> meu-nginx /bin/bash
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Executar como root dentro do container</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> </span><span class="token" style="color:rgb(255, 203, 139)">exec</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-u</span><span> root </span><span class="token parameter" style="color:rgb(214, 222, 235)">-it</span><span> meu-nginx /bin/bash
</span></code></pre></div>

---

## 🐳 Dockerfile (Criar Imagens Customizadas)

**Descrição:** Um arquivo de texto com instruções para construir uma imagem Docker.

### Exemplo Básico

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">dockerfile</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-ftggkersq" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-dockerfile" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Dockerfile</span><span>
</span><span></span><span class="token instruction" style="color:rgb(127, 219, 202)">FROM</span><span class="token instruction"> ubuntu:22.04</span><span>
</span><span></span><span class="token instruction" style="color:rgb(127, 219, 202)">LABEL</span><span class="token instruction"> maintainer=</span><span class="token instruction" style="color:rgb(173, 219, 103)">&quot;alex@exemplo.com&quot;</span><span>
</span><span></span><span class="token instruction" style="color:rgb(127, 219, 202)">RUN</span><span class="token instruction"> apt update &amp;&amp; apt install -y nginx curl &amp;&amp; rm -rf /var/lib/apt/lists/*</span><span>
</span><span></span><span class="token instruction" style="color:rgb(127, 219, 202)">COPY</span><span class="token instruction"> index.html /var/www/html/</span><span>
</span><span></span><span class="token instruction" style="color:rgb(127, 219, 202)">EXPOSE</span><span class="token instruction"> 80</span><span>
</span><span></span><span class="token instruction" style="color:rgb(127, 219, 202)">CMD</span><span class="token instruction"> [</span><span class="token instruction" style="color:rgb(173, 219, 103)">&quot;nginx&quot;</span><span class="token instruction">, </span><span class="token instruction" style="color:rgb(173, 219, 103)">&quot;-g&quot;</span><span class="token instruction">, </span><span class="token instruction" style="color:rgb(173, 219, 103)">&quot;daemon off;&quot;</span><span class="token instruction">]</span><span>
</span></code></pre></div>

### Construir Imagem

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-sgm1d014g" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Criar arquivo index.html</span><span>
</span><span></span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;&lt;h1&gt;Servidor Web Customizado&lt;/h1&gt;&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">&gt;</span><span> index.html
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Construir imagem a partir do Dockerfile no diretório atual</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> build </span><span class="token parameter" style="color:rgb(214, 222, 235)">-t</span><span> meu-webserver:1.0 </span><span class="token" style="color:rgb(255, 203, 139)">.</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Listar imagens</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> images
</span></code></pre></div>

### Executar Imagem Customizada

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-67o8o0hs8" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> run </span><span class="token parameter" style="color:rgb(214, 222, 235)">-d</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">80</span><span>:80 </span><span class="token parameter" style="color:rgb(214, 222, 235)">--name</span><span> meu-site meu-webserver:1.0
</span></code></pre></div>

---

## 🗂️ Volumes (Persistência de Dados)

**Descrição:** Permitem que os dados gerados pelos containers persistam mesmo após o container ser removido.

### Tipos de Volumes

1. **Named Volumes:** Gerenciados pelo Docker.
2. **Bind Mounts:** Mapeiam um diretório do host para o container.

**Exemplos:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-p777qwmfr" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Criar named volume</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> volume create meu-volume-dados
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Executar container usando named volume</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> run </span><span class="token parameter" style="color:rgb(214, 222, 235)">-d</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-v</span><span> meu-volume-dados:/app/data </span><span class="token parameter" style="color:rgb(214, 222, 235)">--name</span><span> app-com-dados ubuntu
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Executar container usando bind mount</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">mkdir</span><span> ~/meus_dados_host
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> run </span><span class="token parameter" style="color:rgb(214, 222, 235)">-d</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-v</span><span> ~/meus_dados_host:/app/data </span><span class="token parameter" style="color:rgb(214, 222, 235)">--name</span><span> app-bind-mount ubuntu
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Inspecionar volume</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> volume inspect meu-volume-dados
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Remover volume</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> volume </span><span class="token" style="color:rgb(130, 170, 255)">rm</span><span> meu-volume-dados
</span></code></pre></div>

---

## 🌐 Redes Docker

**Descrição:** Permitem que containers se comuniquem entre si e com o mundo externo.

### Tipos de Rede

- **Bridge (padrão):** Rede interna para comunicação entre containers no mesmo host.
- **Host:** Container compartilha a pilha de rede do host.
- **None:** Container não tem interface de rede.
- **Overlay:** Para comunicação entre containers em múltiplos hosts (Docker Swarm).

**Exemplos:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-6bja4w0cp" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Listar redes</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> network </span><span class="token" style="color:rgb(130, 170, 255)">ls</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Criar rede bridge customizada</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> network create </span><span class="token parameter" style="color:rgb(214, 222, 235)">--driver</span><span> bridge minha-rede-app
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Executar container em rede customizada</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> run </span><span class="token parameter" style="color:rgb(214, 222, 235)">-d</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">--name</span><span> db-server </span><span class="token parameter" style="color:rgb(214, 222, 235)">--network</span><span> minha-rede-app mysql:8.0
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Conectar container a uma rede existente</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> network connect minha-rede-app meu-webserver
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Inspecionar rede</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> network inspect minha-rede-app
</span></code></pre></div>

---

## 🐙 Docker Compose (Gerenciar Múltiplos Containers)

**Descrição:** Ferramenta para definir e executar aplicações multi-container Docker usando um arquivo YAML.

### Instalação

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-6ev8szxll" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Linux</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">apt</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">install</span><span> docker-compose-plugin </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Para Docker Compose V2</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ou para Docker Compose V1 (legado)</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># sudo curl -L &quot;https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)&quot; -o /usr/local/bin/docker-compose</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># sudo chmod +x /usr/local/bin/docker-compose</span><span>
</span></code></pre></div>

### Exemplo: WordPress + MySQL (`docker-compose.yml`)

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">yaml</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-zxr5psu50" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-yaml" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token key" style="color:rgb(255, 203, 139)">version</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;3.8&#x27;</span><span>
</span>
<span></span><span class="token key" style="color:rgb(255, 203, 139)">services</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>  </span><span class="token key" style="color:rgb(255, 203, 139)">db</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>    </span><span class="token key" style="color:rgb(255, 203, 139)">image</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> mysql</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span class="token" style="color:rgb(247, 140, 108)">8.0</span><span>
</span><span>    </span><span class="token key" style="color:rgb(255, 203, 139)">environment</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>      </span><span class="token key" style="color:rgb(255, 203, 139)">MYSQL_ROOT_PASSWORD</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> senha_root_secreta
</span><span>      </span><span class="token key" style="color:rgb(255, 203, 139)">MYSQL_DATABASE</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> wordpress
</span><span>      </span><span class="token key" style="color:rgb(255, 203, 139)">MYSQL_USER</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> wp_user
</span><span>      </span><span class="token key" style="color:rgb(255, 203, 139)">MYSQL_PASSWORD</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> wp_senha_secreta
</span><span>    </span><span class="token key" style="color:rgb(255, 203, 139)">volumes</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>      </span><span class="token" style="color:rgb(199, 146, 234)">-</span><span> db_data</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>/var/lib/mysql
</span><span>    </span><span class="token key" style="color:rgb(255, 203, 139)">networks</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>      </span><span class="token" style="color:rgb(199, 146, 234)">-</span><span> wp_network
</span>
<span>  </span><span class="token key" style="color:rgb(255, 203, 139)">wordpress</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>    </span><span class="token key" style="color:rgb(255, 203, 139)">image</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> wordpress</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>latest
</span><span>    </span><span class="token key" style="color:rgb(255, 203, 139)">depends_on</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>      </span><span class="token" style="color:rgb(199, 146, 234)">-</span><span> db
</span><span>    </span><span class="token key" style="color:rgb(255, 203, 139)">ports</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>      </span><span class="token" style="color:rgb(199, 146, 234)">-</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;8080:80&quot;</span><span>
</span><span>    </span><span class="token key" style="color:rgb(255, 203, 139)">environment</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>      </span><span class="token key" style="color:rgb(255, 203, 139)">WORDPRESS_DB_HOST</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> db</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span class="token" style="color:rgb(247, 140, 108)">3306</span><span>
</span><span>      </span><span class="token key" style="color:rgb(255, 203, 139)">WORDPRESS_DB_USER</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> wp_user
</span><span>      </span><span class="token key" style="color:rgb(255, 203, 139)">WORDPRESS_DB_PASSWORD</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> wp_senha_secreta
</span><span>      </span><span class="token key" style="color:rgb(255, 203, 139)">WORDPRESS_DB_NAME</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> wordpress
</span><span>    </span><span class="token key" style="color:rgb(255, 203, 139)">volumes</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>      </span><span class="token" style="color:rgb(199, 146, 234)">-</span><span> wp_data</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>/var/www/html
</span><span>    </span><span class="token key" style="color:rgb(255, 203, 139)">networks</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>      </span><span class="token" style="color:rgb(199, 146, 234)">-</span><span> wp_network
</span>
<span></span><span class="token key" style="color:rgb(255, 203, 139)">volumes</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>  </span><span class="token key" style="color:rgb(255, 203, 139)">db_data</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>  </span><span class="token key" style="color:rgb(255, 203, 139)">wp_data</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span>
<span></span><span class="token key" style="color:rgb(255, 203, 139)">networks</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>  </span><span class="token key" style="color:rgb(255, 203, 139)">wp_network</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span></code></pre></div>

**Comandos:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-i3x4e7m5i" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Iniciar serviços (em background)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker-compose</span><span> up </span><span class="token parameter" style="color:rgb(214, 222, 235)">-d</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ver logs de todos os serviços</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker-compose</span><span> logs </span><span class="token parameter" style="color:rgb(214, 222, 235)">-f</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Parar serviços</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker-compose</span><span> stop
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Parar e remover containers, redes e volumes</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker-compose</span><span> down </span><span class="token parameter" style="color:rgb(214, 222, 235)">-v</span><span>
</span></code></pre></div>

---

## 🔒 Docker em Segurança da Informação

### 1. Labs de Vulnerabilidades

**DVWA (Damn Vulnerable Web Application):**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-2p6tckgwq" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> run </span><span class="token parameter" style="color:rgb(214, 222, 235)">-d</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">80</span><span>:80 vulnerables/web-dvwa
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Acessar: http://localhost/setup.php (admin:password)</span><span>
</span></code></pre></div>

**OWASP Juice Shop:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-5iq911xzm" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> run </span><span class="token parameter" style="color:rgb(214, 222, 235)">--rm</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">3000</span><span>:3000 bkimminich/juice-shop
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Acessar: http://localhost:3000</span><span>
</span></code></pre></div>

**Metasploitable 2:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-mweg62hzw" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> run </span><span class="token parameter" style="color:rgb(214, 222, 235)">-d</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">21</span><span>:21 </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">22</span><span>:22 </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">80</span><span>:80 </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">139</span><span>:139 </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">445</span><span>:445 </span><span class="token parameter" style="color:rgb(214, 222, 235)">--name</span><span> metasploitable2 tleemcjr/metasploitable2:latest
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Credenciais: msfadmin:msfadmin</span><span>
</span></code></pre></div>

---

### 2. Ferramentas de Pentest

**Kali Linux:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-13z0j49rp" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> pull kalilinux/kali-rolling
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> run </span><span class="token parameter" style="color:rgb(214, 222, 235)">--memory</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span>1g </span><span class="token parameter" style="color:rgb(214, 222, 235)">-it</span><span> kalilinux/kali-rolling /bin/bash
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Instalar ferramentas: apt install net-tools hping3 tcpdump netcat-traditional -y</span><span>
</span></code></pre></div>

**OWASP ZAP:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-y7yd1taxl" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> run </span><span class="token parameter" style="color:rgb(214, 222, 235)">-u</span><span> zap </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">8080</span><span>:8080 </span><span class="token parameter" style="color:rgb(214, 222, 235)">-i</span><span> owasp/zap2docker-stable zap-webswing.sh
</span></code></pre></div>

---

### 3. Análise de Malware (Sandbox)

**REMnux:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-8zy732wnx" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> pull remnux/remnux-distro
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> run </span><span class="token parameter" style="color:rgb(214, 222, 235)">-it</span><span> remnux/remnux-distro /bin/bash
</span></code></pre></div>

---

### 4. SIEM (Wazuh)

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-u9dn74adm" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> pull wazuh/wazuh
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> run </span><span class="token parameter" style="color:rgb(214, 222, 235)">-d</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">--name</span><span> wazuh-manager </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">1514</span><span>:1514/udp </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">1515</span><span>:1515 </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">55000</span><span>:55000 wazuh/wazuh
</span></code></pre></div>

---

## 🔗 Links Relacionados

- [[01_Introducao-ao-Linux]]
- [[19_Hardening-Linux]]
- [[27_Apache]]
- [[28_MySQL]]
- [[29_PostgreSQL]]
- [[34_LVM]]
- [[Virtualizacao]] (na pasta Segurança/Recursos)

---

## 📚 Referências

- Docker Official: [www.docker.com](https://www.docker.com/)
- Docker Hub: [hub.docker.com](https://hub.docker.com/)
- Docker Docs: [docs.docker.com](https://docs.docker.com/)
- Docker Compose Docs: [docs.docker.com/compose](https://docs.docker.com/compose/)