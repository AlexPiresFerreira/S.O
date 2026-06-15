
# 🐚 Bash Scripting no Linux

> **Tags:** #linux #bash #scripting #automacao #shell #programacao

---

## 📌 Visão Geral

**Bash Scripting** é a arte de escrever scripts para automatizar tarefas no terminal Linux.

🎯 **Objetivo:** Criar scripts para automação de tarefas administrativas, de segurança e de desenvolvimento.

---

## 🚀 Sintaxe Básica

### Shebang

**Descrição:** A primeira linha do script, indica qual interpretador usar.

bash
#### !/bin/bash


---

### Comentários

**Descrição:** Linhas que começam com `#` são ignoradas.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-v413qen3b" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Este é um comentário</span><span>
</span><span></span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Olá&quot;</span><span> </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Este também é um comentário</span><span>
</span></code></pre></div>

---

### Extensão e Permissões

**Extensão:** `.sh` (convenção, não obrigatório).

**Permissão de execução:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-f3v9lrhmc" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">chmod</span><span> +x meu_script.sh
</span></code></pre></div>

**Executar:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-fjmgdy03o" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span>./meu_script.sh
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">bash</span><span> meu_script.sh
</span></code></pre></div>

---

## 🔤 Variáveis

### Declaração e Uso

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-69gpedtts" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Declaração (sem espaços ao redor do =)</span><span>
</span><span></span><span class="token assign-left" style="color:rgb(214, 222, 235)">NOME</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span class="token" style="color:rgb(173, 219, 103)">&quot;Alex&quot;</span><span>
</span><span></span><span class="token assign-left" style="color:rgb(214, 222, 235)">IDADE</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span class="token" style="color:rgb(247, 140, 108)">39</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Uso (com $)</span><span>
</span><span></span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Olá, </span><span class="token" style="color:rgb(214, 222, 235)">$NOME</span><span class="token" style="color:rgb(173, 219, 103)">!&quot;</span><span>
</span><span></span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Você tem </span><span class="token" style="color:rgb(214, 222, 235)">$IDADE</span><span class="token" style="color:rgb(173, 219, 103)"> anos.&quot;</span><span>
</span></code></pre></div>

---

### Variáveis de Ambiente

**Descrição:** Variáveis predefinidas pelo sistema.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-vxvbiuh73" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token environment" style="color:rgb(130, 170, 255)">$PATH</span><span>
</span><span></span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token environment" style="color:rgb(130, 170, 255)">$HOME</span><span>
</span><span></span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token environment" style="color:rgb(130, 170, 255)">$USER</span><span>
</span><span></span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token environment" style="color:rgb(130, 170, 255)">$SHELL</span><span>
</span></code></pre></div>

---

### Input do Usuário (read)

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-gswgy3188" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Qual é o seu nome?&quot;</span><span>
</span><span></span><span class="token" style="color:rgb(255, 203, 139)">read</span><span> NOME_USUARIO
</span><span></span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Olá, </span><span class="token" style="color:rgb(214, 222, 235)">$NOME_USUARIO</span><span class="token" style="color:rgb(173, 219, 103)">!&quot;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Input com prompt</span><span>
</span><span></span><span class="token" style="color:rgb(255, 203, 139)">read</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Digite sua idade: &quot;</span><span> IDADE_USUARIO
</span><span></span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Sua idade é: </span><span class="token" style="color:rgb(214, 222, 235)">$IDADE_USUARIO</span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span>
</span></code></pre></div>

---

## ⚙️ Operadores

### Operadores Aritméticos

**Sintaxe:** `((expressão))` ou `$[expressão]` ou `expr`

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-bp50qwj04" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token assign-left" style="color:rgb(214, 222, 235)">NUM1</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span class="token" style="color:rgb(247, 140, 108)">10</span><span>
</span><span></span><span class="token assign-left" style="color:rgb(214, 222, 235)">NUM2</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span class="token" style="color:rgb(247, 140, 108)">5</span><span>
</span>
<span></span><span class="token assign-left" style="color:rgb(214, 222, 235)">SOMA</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span class="token" style="color:rgb(214, 222, 235)">$((</span><span class="token" style="color:rgb(214, 222, 235)">NUM1 </span><span class="token" style="color:rgb(127, 219, 202)">+</span><span class="token" style="color:rgb(214, 222, 235)"> NUM2</span><span class="token" style="color:rgb(214, 222, 235)">))</span><span>
</span><span></span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Soma: </span><span class="token" style="color:rgb(214, 222, 235)">$SOMA</span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span>
</span>
<span></span><span class="token assign-left" style="color:rgb(214, 222, 235)">SUBTRACAO</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span>$</span><span class="token" style="color:rgb(199, 146, 234)">[</span><span>NUM1 - NUM2</span><span class="token" style="color:rgb(199, 146, 234)">]</span><span>
</span><span></span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Subtração: </span><span class="token" style="color:rgb(214, 222, 235)">$SUBTRACAO</span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span>
</span>
<span></span><span class="token assign-left" style="color:rgb(214, 222, 235)">MULTIPLICACAO</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span class="token" style="color:rgb(214, 222, 235)">$(</span><span class="token" style="color:rgb(130, 170, 255)">expr</span><span class="token" style="color:rgb(214, 222, 235)"> $NUM1 </span><span class="token" style="color:rgb(199, 146, 234)">\</span><span class="token" style="color:rgb(214, 222, 235)">* $NUM2</span><span class="token" style="color:rgb(214, 222, 235)">)</span><span> </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Usar \ para *</span><span>
</span><span></span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Multiplicação: </span><span class="token" style="color:rgb(214, 222, 235)">$MULTIPLICACAO</span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span>
</span></code></pre></div>

---

### Operadores de Comparação (para `if`)

| Operador | Descrição |
|----------|-----------|
| `-eq` | Igual a (equal) |
| `-ne` | Diferente de (not equal) |
| `-gt` | Maior que (greater than) |
| `-ge` | Maior ou igual a (greater or equal) |
| `-lt` | Menor que (less than) |
| `-le` | Menor ou igual a (less or equal) |

---

### Operadores de String (para `if`)

| Operador | Descrição |
|----------|-----------|
| `==` | Igual a |
| `!=` | Diferente de |
| `-z` | String é vazia |
| `-n` | String não é vazia |

---

## 📝 Estruturas de Controle

### if / else if / else

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-rxit6epmo" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token shebang" style="color:rgb(214, 222, 235);font-weight:bold">#!/bin/bash</span><span>
</span>
<span></span><span class="token" style="color:rgb(255, 203, 139)">read</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Digite sua idade: &quot;</span><span> IDADE
</span>
<span></span><span class="token" style="color:rgb(127, 219, 202)">if</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">[</span><span> </span><span class="token" style="color:rgb(214, 222, 235)">$IDADE</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-ge</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">18</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">]</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">then</span><span>
</span><span>    </span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Você é maior de idade.&quot;</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">elif</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">[</span><span> </span><span class="token" style="color:rgb(214, 222, 235)">$IDADE</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-ge</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">13</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">]</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">then</span><span>
</span><span>    </span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Você é adolescente.&quot;</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">else</span><span>
</span><span>    </span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Você é criança.&quot;</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">fi</span><span>
</span></code></pre></div>

---

### case

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-p67t2mtei" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token shebang" style="color:rgb(214, 222, 235);font-weight:bold">#!/bin/bash</span><span>
</span>
<span></span><span class="token" style="color:rgb(255, 203, 139)">read</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Digite uma fruta: &quot;</span><span> FRUTA
</span>
<span></span><span class="token" style="color:rgb(127, 219, 202)">case</span><span> </span><span class="token" style="color:rgb(214, 222, 235)">$FRUTA</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">in</span><span>
</span><span>    </span><span class="token" style="color:rgb(173, 219, 103)">&quot;maçã&quot;</span><span class="token" style="color:rgb(127, 219, 202)">|</span><span class="token" style="color:rgb(173, 219, 103)">&quot;pera&quot;</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span>        </span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;É uma fruta de clima temperado.&quot;</span><span>
</span><span>        </span><span class="token" style="color:rgb(199, 146, 234)">;</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span><span>    </span><span class="token" style="color:rgb(173, 219, 103)">&quot;banana&quot;</span><span class="token" style="color:rgb(127, 219, 202)">|</span><span class="token" style="color:rgb(173, 219, 103)">&quot;manga&quot;</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span>        </span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;É uma fruta tropical.&quot;</span><span>
</span><span>        </span><span class="token" style="color:rgb(199, 146, 234)">;</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span><span>    *</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span>        </span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Não sei que fruta é essa.&quot;</span><span>
</span><span>        </span><span class="token" style="color:rgb(199, 146, 234)">;</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">esac</span><span>
</span></code></pre></div>

---

### for Loop

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-kg59tpasl" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token shebang" style="color:rgb(214, 222, 235);font-weight:bold">#!/bin/bash</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Loop com lista</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">for</span><span> </span><span class="token for-or-select" style="color:rgb(214, 222, 235)">FRUTA</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">in</span><span> maçã banana laranja</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">do</span><span>
</span><span>    </span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Eu gosto de </span><span class="token" style="color:rgb(214, 222, 235)">$FRUTA</span><span class="token" style="color:rgb(173, 219, 103)">.&quot;</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">done</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Loop com range numérico</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">for</span><span> </span><span class="token for-or-select" style="color:rgb(214, 222, 235)">i</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">in</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">{</span><span class="token" style="color:rgb(247, 140, 108)">1</span><span class="token" style="color:rgb(199, 146, 234)">..</span><span class="token" style="color:rgb(247, 140, 108)">5</span><span class="token" style="color:rgb(199, 146, 234)">}</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">do</span><span>
</span><span>    </span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Número: </span><span class="token" style="color:rgb(214, 222, 235)">$i</span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">done</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Loop com saída de comando</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">for</span><span> </span><span class="token for-or-select" style="color:rgb(214, 222, 235)">ARQUIVO</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">in</span><span> </span><span class="token" style="color:rgb(214, 222, 235)">$(</span><span class="token" style="color:rgb(130, 170, 255)">ls</span><span class="token" style="color:rgb(214, 222, 235)"> *.txt</span><span class="token" style="color:rgb(214, 222, 235)">)</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">do</span><span>
</span><span>    </span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Processando arquivo: </span><span class="token" style="color:rgb(214, 222, 235)">$ARQUIVO</span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">done</span><span>
</span></code></pre></div>

---

### while Loop

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-nqu0hcjdn" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token shebang" style="color:rgb(214, 222, 235);font-weight:bold">#!/bin/bash</span><span>
</span>
<span></span><span class="token assign-left" style="color:rgb(214, 222, 235)">CONTADOR</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span class="token" style="color:rgb(247, 140, 108)">1</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">while</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">[</span><span> </span><span class="token" style="color:rgb(214, 222, 235)">$CONTADOR</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-le</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">5</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">]</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">do</span><span>
</span><span>    </span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Contador: </span><span class="token" style="color:rgb(214, 222, 235)">$CONTADOR</span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span>
</span><span>    </span><span class="token assign-left" style="color:rgb(214, 222, 235)">CONTADOR</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span class="token" style="color:rgb(214, 222, 235)">$((</span><span class="token" style="color:rgb(214, 222, 235)">CONTADOR </span><span class="token" style="color:rgb(127, 219, 202)">+</span><span class="token" style="color:rgb(214, 222, 235)"> </span><span class="token" style="color:rgb(247, 140, 108)">1</span><span class="token" style="color:rgb(214, 222, 235)">))</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">done</span><span>
</span></code></pre></div>

---

## 📊 Funções

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-944e9b5td" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token shebang" style="color:rgb(214, 222, 235);font-weight:bold">#!/bin/bash</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Declaração de função</span><span>
</span><span></span><span class="token function-name" style="color:rgb(130, 170, 255)">minha_funcao</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">{</span><span>
</span><span>    </span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Esta é minha primeira função.&quot;</span><span>
</span><span>    </span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Recebi o argumento: </span><span class="token" style="color:rgb(214, 222, 235)">$1</span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span>
</span><span></span><span class="token" style="color:rgb(199, 146, 234)">}</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Chamar função</span><span>
</span><span>minha_funcao </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Olá!&quot;</span><span>
</span></code></pre></div>

---

## 🔗 Redirecionamento e Pipes

### Redirecionamento

| Operador | Descrição |
|----------|-----------|
| `>` | Redireciona saída (sobrescreve) |
| `>>` | Redireciona saída (append) |
| `2>` | Redireciona erro |
| `&>` | Redireciona saída e erro |
| `<` | Redireciona entrada |

**Exemplos:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-9b8lczqa7" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Log de erro&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">&gt;</span><span> erro.log
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">ls</span><span> /diretorio_inexistente </span><span class="token file-descriptor" style="color:rgb(214, 222, 235);font-weight:bold">2</span><span class="token" style="color:rgb(127, 219, 202)">&gt;&gt;</span><span> erro.log
</span></code></pre></div>

---

### Pipes (`|`)

**Descrição:** Conecta a saída de um comando à entrada de outro.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-j6ex3u651" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">ls</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-l</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">grep</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;.txt&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">wc</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-l</span><span>
</span></code></pre></div>

---

## ⚙️ Execução de Comandos

### Subshell (`$()`)

**Descrição:** Executa um comando e substitui sua saída no script.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-xucfxpn57" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token assign-left" style="color:rgb(214, 222, 235)">DATA_ATUAL</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span class="token" style="color:rgb(214, 222, 235)">$(</span><span class="token" style="color:rgb(130, 170, 255)">date</span><span class="token" style="color:rgb(214, 222, 235)"> +%F</span><span class="token" style="color:rgb(214, 222, 235)">)</span><span>
</span><span></span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Hoje é: </span><span class="token" style="color:rgb(214, 222, 235)">$DATA_ATUAL</span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span>
</span>
<span></span><span class="token assign-left" style="color:rgb(214, 222, 235)">NUM_ARQUIVOS</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span class="token" style="color:rgb(214, 222, 235)">$(</span><span class="token" style="color:rgb(130, 170, 255)">ls</span><span class="token" style="color:rgb(214, 222, 235)"> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-l</span><span class="token" style="color:rgb(214, 222, 235)"> </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span class="token" style="color:rgb(214, 222, 235)"> </span><span class="token" style="color:rgb(130, 170, 255)">wc</span><span class="token" style="color:rgb(214, 222, 235)"> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-l</span><span class="token" style="color:rgb(214, 222, 235)">)</span><span>
</span><span></span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Número de arquivos: </span><span class="token" style="color:rgb(214, 222, 235)">$NUM_ARQUIVOS</span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span>
</span></code></pre></div>

---

### Backticks (`` ` ``)

**Descrição:** Similar ao subshell, mas mais antigo e menos recomendado.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-4lds0hq7o" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token assign-left" style="color:rgb(214, 222, 235)">DATA_ATUAL</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span class="token" style="color:rgb(214, 222, 235)">`</span><span class="token" style="color:rgb(130, 170, 255)">date</span><span class="token" style="color:rgb(214, 222, 235)"> +%F</span><span class="token" style="color:rgb(214, 222, 235)">`</span><span>
</span></code></pre></div>

---

## ⚠️ Dicas e Boas Práticas

- **Caminhos absolutos:** Use `/usr/bin/comando` em vez de `comando` em scripts agendados.
- **Variáveis:** Use aspas duplas (`"$VAR"`) para evitar problemas com espaços.
- **`set -e`:** Sai do script se um comando falhar.
- **`set -x`:** Exibe os comandos sendo executados (debug).
- **`trap`:** Captura sinais (Ctrl+C) para limpeza.

---

## 🔗 Links Relacionados

- [[24_AWK-Avancado]]
- [[25_Expressoes-Regulares]]
- [[26_Automacao]]
- [[03_Comandos-Basicos]]
- [[04_Gerenciamento-de-Arquivos]]

---

## 📚 Referências

- Advanced Bash-Scripting Guide: [tldp.org/LDP/abs/html](https://tldp.org/LDP/abs/html/)
- Bash Guide for Beginners: [tldp.org/LDP/Bash-Beginners-Guide/html](https://tldp.org/LDP/Bash-Beginners-Guide/html/)
- Shellcheck (linter para scripts): [www.shellcheck.net](https://www.shellcheck.net/)
