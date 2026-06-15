
# 💻 Comandos Básicos do Linux

> **Tags:** #linux #comandos #basicos #terminal #shell

---

## 📌 Visão Geral

Comandos essenciais para navegação e manipulação de arquivos no Linux.

🎯 **Objetivo:** Dominar os comandos básicos para uso diário do terminal.

---

## 🗂️ Navegação de Diretórios

### pwd (Print Working Directory)

**Descrição:** Exibe o diretório atual.

bash pwd

```
**Output:**
```

/home/usuario

---
### cd (Change Directory)

**Descrição:** Navega entre diretórios.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-spuc2anj1" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ir para home</span><span>
</span><span></span><span class="token" style="color:rgb(255, 203, 139)">cd</span><span> ~
</span><span></span><span class="token" style="color:rgb(255, 203, 139)">cd</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ir para raiz</span><span>
</span><span></span><span class="token" style="color:rgb(255, 203, 139)">cd</span><span> /
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Voltar ao diretório anterior</span><span>
</span><span></span><span class="token" style="color:rgb(255, 203, 139)">cd</span><span> -
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Subir um nível</span><span>
</span><span></span><span class="token" style="color:rgb(255, 203, 139)">cd</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">..</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ir para diretório específico</span><span>
</span><span></span><span class="token" style="color:rgb(255, 203, 139)">cd</span><span> /var/log
</span></code></pre></div>

---

### ls (List)

**Descrição:** Lista arquivos e diretórios.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-p9szh97kk" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Listagem simples</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">ls</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Listagem detalhada</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">ls</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-l</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Incluir arquivos ocultos</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">ls</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-a</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Listagem detalhada + ocultos</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">ls</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-la</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Tamanho em formato legível</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">ls</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-lh</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ordenar por data de modificação</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">ls</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-lt</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ordenar por tamanho</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">ls</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-lS</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Recursivo (subdiretórios)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">ls</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-R</span><span>
</span></code></pre></div>

**Entendendo `ls -l`:**
```

-rw-r--r-- 1 usuario grupo 1234 Jan 03 10:30 arquivo.txt │ │ │ │ │ │ │ │ │ │ │ │ │ └─ Nome │ │ │ │ │ └────────────── Data/Hora │ │ │ │ └─────────────────── Tamanho (bytes) │ │ │ └───────────────────────── Grupo │ │ └───────────────────────────────── Proprietário │ └─────────────────────────────────── Número de links └────────────────────────────────────────────── Permissões

```
---

## 📁 Criação e Remoção

### mkdir (Make Directory)

**Descrição:** Cria diretórios.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-d8mbijs6y" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Criar diretório</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">mkdir</span><span> pasta
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Criar diretório com espaços (usar aspas)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">mkdir</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;minha pasta&#x27;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Criar estrutura de diretórios</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">mkdir</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> /home/usuario/projetos/linux/scripts
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Criar múltiplos diretórios</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">mkdir</span><span> pasta1 pasta2 pasta3
</span></code></pre></div>

---

### touch

**Descrição:** Cria arquivos vazios ou atualiza timestamp.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-7xhsvru7t" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Criar arquivo</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">touch</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Criar múltiplos arquivos</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">touch</span><span> arquivo1.txt arquivo2.txt arquivo3.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Atualizar timestamp de arquivo existente</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">touch</span><span> arquivo_existente.txt
</span></code></pre></div>

---

### rmdir (Remove Directory)

**Descrição:** Remove diretórios **vazios**.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-ebbegergy" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Remover diretório vazio</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">rmdir</span><span> pasta_vazia
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Remover múltiplos diretórios vazios</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">rmdir</span><span> pasta1 pasta2 pasta3
</span></code></pre></div>

---

### rm (Remove)

**Descrição:** Remove arquivos e diretórios.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-h73k6ok84" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Remover arquivo</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">rm</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Remover múltiplos arquivos</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">rm</span><span> arquivo1.txt arquivo2.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Remover diretório e conteúdo (recursivo)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">rm</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-r</span><span> pasta/
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Remover forçadamente (sem confirmação)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">rm</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-f</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Remover diretório e conteúdo forçadamente</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">rm</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-rf</span><span> pasta/
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Remover com confirmação</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">rm</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-i</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Remover com verbose (mostrar o que está sendo removido)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">rm</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-v</span><span> arquivo.txt
</span></code></pre></div>

**⚠️ ATENÇÃO:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-djafduv4s" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># NUNCA EXECUTE ISSO! (Remove tudo do sistema)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">rm</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-rf</span><span> /
</span></code></pre></div>

---

## 📋 Cópia e Movimentação

### cp (Copy)

**Descrição:** Copia arquivos e diretórios.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-6wv1lpb6r" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Copiar arquivo</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">cp</span><span> origem.txt destino.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Copiar para outro diretório</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">cp</span><span> arquivo.txt /home/usuario/documentos/
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Copiar múltiplos arquivos para diretório</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">cp</span><span> arquivo1.txt arquivo2.txt /destino/
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Copiar diretório e conteúdo (recursivo)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">cp</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-r</span><span> pasta_origem/ pasta_destino/
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Copiar com confirmação antes de sobrescrever</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">cp</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-i</span><span> origem.txt destino.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Copiar preservando atributos (permissões, timestamps)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">cp</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> arquivo.txt copia.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Copiar com verbose</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">cp</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-v</span><span> origem.txt destino.txt
</span></code></pre></div>

---

### mv (Move)

**Descrição:** Move ou renomeia arquivos/diretórios.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-2micstpt9" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Mover arquivo</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">mv</span><span> arquivo.txt /home/usuario/documentos/
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Renomear arquivo</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">mv</span><span> nome_antigo.txt nome_novo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Mover múltiplos arquivos</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">mv</span><span> arquivo1.txt arquivo2.txt /destino/
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Mover diretório</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">mv</span><span> pasta_origem/ /novo/local/
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Mover com confirmação</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">mv</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-i</span><span> origem.txt destino.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Mover com verbose</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">mv</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-v</span><span> origem.txt destino.txt
</span></code></pre></div>

---

## 🔍 Busca e Localização

### find

**Descrição:** Busca arquivos e diretórios.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-6jkzd9co3" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Buscar por nome</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">find</span><span> /home </span><span class="token parameter" style="color:rgb(214, 222, 235)">-name</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;arquivo.txt&quot;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Buscar ignorando case</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">find</span><span> /home </span><span class="token parameter" style="color:rgb(214, 222, 235)">-iname</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;arquivo.txt&quot;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Buscar por tipo (f=arquivo, d=diretório)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">find</span><span> /home </span><span class="token parameter" style="color:rgb(214, 222, 235)">-type</span><span> f </span><span class="token parameter" style="color:rgb(214, 222, 235)">-name</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;*.txt&quot;</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">find</span><span> /home </span><span class="token parameter" style="color:rgb(214, 222, 235)">-type</span><span> d </span><span class="token parameter" style="color:rgb(214, 222, 235)">-name</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;projetos&quot;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Buscar por tamanho</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">find</span><span> /home </span><span class="token parameter" style="color:rgb(214, 222, 235)">-size</span><span> +100M  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Maior que 100MB</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">find</span><span> /home </span><span class="token parameter" style="color:rgb(214, 222, 235)">-size</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-1M</span><span>    </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Menor que 1MB</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Buscar por data de modificação</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">find</span><span> /home </span><span class="token parameter" style="color:rgb(214, 222, 235)">-mtime</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-7</span><span>    </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Modificado nos últimos 7 dias</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">find</span><span> /home </span><span class="token parameter" style="color:rgb(214, 222, 235)">-mtime</span><span> +30   </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Modificado há mais de 30 dias</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Buscar por proprietário</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">find</span><span> / </span><span class="token parameter" style="color:rgb(214, 222, 235)">-user</span><span> usuario
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Buscar por grupo</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">find</span><span> / </span><span class="token parameter" style="color:rgb(214, 222, 235)">-group</span><span> grupo
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Buscar e executar comando</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">find</span><span> /home </span><span class="token parameter" style="color:rgb(214, 222, 235)">-name</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;*.log&quot;</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-exec</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">rm</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">{</span><span class="token" style="color:rgb(199, 146, 234)">}</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">\</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Buscar e listar detalhado</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">find</span><span> /home </span><span class="token parameter" style="color:rgb(214, 222, 235)">-name</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;*.txt&quot;</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-ls</span><span>
</span></code></pre></div>

---

### locate

**Descrição:** Busca rápida por nome (usa banco de dados).

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-nvj6py8lc" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Instalar (se necessário)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">apt</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">install</span><span> mlocate  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Debian/Ubuntu</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> yum </span><span class="token" style="color:rgb(130, 170, 255)">install</span><span> mlocate  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Red Hat/CentOS</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Atualizar banco de dados</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> updatedb
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Buscar arquivo</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">locate</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Buscar ignorando case</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">locate</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-i</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Limitar número de resultados</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">locate</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-n</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">10</span><span> arquivo.txt
</span></code></pre></div>

---

### which

**Descrição:** Localiza executável no PATH.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-jcilxhh1p" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Localizar comando</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">which</span><span> python
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">which</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">bash</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">which</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">ls</span><span>
</span></code></pre></div>

**Output:**
```

/usr/bin/python /bin/bash /bin/ls

```
---

### whereis

**Descrição:** Localiza binário, código-fonte e manual.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-090texsvq" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">whereis</span><span> python
</span></code></pre></div>

**Output:**
```

python: /usr/bin/python /usr/lib/python2.7 /usr/share/man/man1/python.1.gz

```
---

## 📄 Visualização de Arquivos

### cat (Concatenate)

**Descrição:** Exibe conteúdo de arquivos.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-gagdmu65z" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Exibir arquivo</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">cat</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Exibir múltiplos arquivos</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">cat</span><span> arquivo1.txt arquivo2.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Numerar linhas</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">cat</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-n</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Exibir caracteres não imprimíveis</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">cat</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-A</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Concatenar arquivos em novo arquivo</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">cat</span><span> arquivo1.txt arquivo2.txt </span><span class="token" style="color:rgb(127, 219, 202)">&gt;</span><span> arquivo_completo.txt
</span></code></pre></div>

---

### less

**Descrição:** Visualizador de arquivos (paginado).

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-0jitfbsvr" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">less</span><span> arquivo.txt
</span></code></pre></div>

**Navegação no less:**
- `Espaço` ou `Page Down`: Próxima página
- `b` ou `Page Up`: Página anterior
- `/palavra`: Buscar "palavra"
- `n`: Próxima ocorrência
- `N`: Ocorrência anterior
- `q`: Sair

---

### more

**Descrição:** Visualizador de arquivos (mais simples que less).

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-u9hva0t8o" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">more</span><span> arquivo.txt
</span></code></pre></div>

---

### head

**Descrição:** Exibe primeiras linhas de arquivo.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-ftzxie3a5" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Primeiras 10 linhas (padrão)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">head</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Primeiras 20 linhas</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">head</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-n</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">20</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Primeira linha</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">head</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-n</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">1</span><span> arquivo.txt
</span></code></pre></div>

---

### tail

**Descrição:** Exibe últimas linhas de arquivo.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-zdbfpsq17" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Últimas 10 linhas (padrão)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">tail</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Últimas 20 linhas</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">tail</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-n</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">20</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Última linha</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">tail</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-n</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">1</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Monitorar arquivo em tempo real (logs)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">tail</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-f</span><span> /var/log/syslog
</span></code></pre></div>

---

## 🔎 Busca em Conteúdo

### grep

**Descrição:** Busca padrões em arquivos.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-oo71bubxn" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Buscar palavra em arquivo</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">grep</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;palavra&quot;</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Buscar ignorando case</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">grep</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-i</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;palavra&quot;</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Buscar recursivamente em diretório</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">grep</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-r</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;palavra&quot;</span><span> /home/usuario/
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Mostrar número da linha</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">grep</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-n</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;palavra&quot;</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Inverter busca (linhas que NÃO contêm)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">grep</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-v</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;palavra&quot;</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Contar ocorrências</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">grep</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-c</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;palavra&quot;</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Buscar com regex</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">grep</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-E</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;palavra[0-9]+&quot;</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Buscar em múltiplos arquivos</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">grep</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;palavra&quot;</span><span> *.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Buscar e mostrar contexto</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">grep</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-C</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">3</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;palavra&quot;</span><span> arquivo.txt  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># 3 linhas antes e depois</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">grep</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-A</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">5</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;palavra&quot;</span><span> arquivo.txt  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># 5 linhas após</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">grep</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-B</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">2</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;palavra&quot;</span><span> arquivo.txt  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># 2 linhas antes</span><span>
</span></code></pre></div>

---

## 📊 Informações de Arquivos

### file

**Descrição:** Identifica tipo de arquivo.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-9ldh218qy" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">file</span><span> arquivo.txt
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">file</span><span> imagem.jpg
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">file</span><span> script.sh
</span></code></pre></div>

**Output:**
```

arquivo.txt: ASCII text imagem.jpg: JPEG image data script.sh: Bourne-Again shell script, ASCII text executable

```
---

### stat

**Descrição:** Exibe informações detalhadas de arquivo.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-9d2rg3rg7" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">stat</span><span> arquivo.txt
</span></code></pre></div>

**Output:**
```

File: arquivo.txt Size: 1234 Blocks: 8 IO Block: 4096 regular file Device: 801h/2049d Inode: 123456 Links: 1 Access: (0644/-rw-r--r--) Uid: ( 1000/ usuario) Gid: ( 1000/ usuario) Access: 2025-01-03 10:30:00.000000000 -0300 Modify: 2025-01-03 10:30:00.000000000 -0300 Change: 2025-01-03 10:30:00.000000000 -0300 Birth: -

```
---

### wc (Word Count)

**Descrição:** Conta linhas, palavras e caracteres.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-niyb53qtm" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Contar linhas</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">wc</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-l</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Contar palavras</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">wc</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-w</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Contar caracteres</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">wc</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-c</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Contar tudo</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">wc</span><span> arquivo.txt
</span></code></pre></div>

**Output:**
```

10 50 300 arquivo.txt │ │ │ │ │ └─ Caracteres │ └───── Palavras └───────── Linhas

```
---

## 🔗 Links Relacionados

- [[02_Estrutura-de-Diretorios]]
- [[04_Gerenciamento-de-Arquivos]]
- [[05_Permissoes-Linux]]
- [[23_Bash-Scripting]]

---

## 📚 Referências

- Linux Command Line: [linuxcommand.org](http://linuxcommand.org/)
- Explain Shell: [explainshell.com](https://explainshell.com/)
- TLDR Pages: [tldr.sh](https://tldr.sh/)