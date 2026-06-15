# 📄 Gerenciamento de Arquivos no Linux

> **Tags:** #linux #arquivos #manipulacao #texto #redirecionamento

---

## 📌 Visão Geral

Comandos avançados para manipulação, visualização e processamento de arquivos de texto no Linux.

🎯 **Objetivo:** Dominar técnicas de manipulação de arquivos para análise de logs, processamento de dados e automação.

---

## 📊 Redirecionamento

### Operadores de Redirecionamento

| Operador | Descrição | Exemplo |
|----------|-----------|---------|
| `>` | Redireciona saída (sobrescreve) | `echo "texto" > arquivo.txt` |
| `>>` | Redireciona saída (append) | `echo "texto" >> arquivo.txt` |
| `<` | Redireciona entrada | `comando < arquivo.txt` |
| `2>` | Redireciona erro | `comando 2> erro.log` |
| `&>` | Redireciona saída e erro | `comando &> tudo.log` |
| `\|` | Pipe (saída de um comando vira entrada de outro) | `cat arquivo.txt \| grep "palavra"` |

---

### Exemplos Práticos

bash
##### Criar arquivo com conteúdo

echo "Olá, mundo!" > arquivo.txt
##### Adicionar ao final do arquivo

echo "Segunda linha" >> arquivo.txt
##### Redirecionar erro

ls /diretorio_inexistente 2> erro.log
##### Redirecionar saída e erro

comando &> tudo.log

# Descartar saída (enviar para /dev/null)

comando > /dev/null 2>&1

---

## 🔗 Pipes (|)

**Descrição:** Conecta a saída de um comando à entrada de outro.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-n31psyn2t" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Listar arquivos e contar</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">ls</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-l</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">wc</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-l</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Buscar processo e filtrar</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">ps</span><span> aux </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">grep</span><span> apache
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ordenar e pegar top 10</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">cat</span><span> arquivo.txt </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">sort</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">head</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-n10</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Múltiplos pipes</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">cat</span><span> access.log </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">grep</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;192.168.1.10&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">cut</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-d</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot; &quot;</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-f7</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">sort</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">uniq</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-c</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">sort</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-nr</span><span>
</span></code></pre></div>

---

## 🔍 Comandos de Busca e Filtro

### grep (Global Regular Expression Print)

**Descrição:** Busca padrões em arquivos.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-i3r5kul1v" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Busca simples</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">grep</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;palavra&quot;</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ignorar case</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">grep</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-i</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;palavra&quot;</span><span> arquivo.txt
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
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Busca recursiva em diretório</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">grep</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-r</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;palavra&quot;</span><span> /var/log/
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Busca com contexto</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">grep</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-C</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">3</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;palavra&quot;</span><span> arquivo.txt  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># 3 linhas antes e depois</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">grep</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-A</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">5</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;palavra&quot;</span><span> arquivo.txt  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># 5 linhas após</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">grep</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-B</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">2</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;palavra&quot;</span><span> arquivo.txt  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># 2 linhas antes</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Busca com regex</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">grep</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-E</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;palavra[0-9]+&quot;</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Busca em múltiplos arquivos</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">grep</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;palavra&quot;</span><span> *.txt
</span></code></pre></div>

---

### sed (Stream Editor)

**Descrição:** Editor de texto em stream (processamento de texto).

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-sje6r9k86" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Substituir palavra (temporário)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sed</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;s/antiga/nova/&#x27;</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Substituir palavra (permanente)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sed</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-i</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;s/antiga/nova/&#x27;</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Substituir todas as ocorrências na linha</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sed</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;s/antiga/nova/g&#x27;</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Substituir apenas na linha 5</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sed</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;5s/antiga/nova/&#x27;</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Deletar linha 3</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sed</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;3d&#x27;</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Deletar linhas 2-5</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sed</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;2,5d&#x27;</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Deletar linhas que contêm &quot;palavra&quot;</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sed</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;/palavra/d&#x27;</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Imprimir apenas linha 10</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sed</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-n</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;10p&#x27;</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Imprimir linhas 5-10</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sed</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-n</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;5,10p&#x27;</span><span> arquivo.txt
</span></code></pre></div>

---

### awk (Aho, Weinberger, Kernighan)

**Descrição:** Linguagem de processamento de texto poderosa.

Ver detalhes completos em: [[24_AWK-Avancado]]

**Sintaxe básica:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-1nv1ycl99" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">awk</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;{print}&#x27;</span><span> arquivo.txt
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">awk</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;{print $1}&#x27;</span><span> arquivo.txt
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">awk</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;{print $1, $3}&#x27;</span><span> arquivo.txt
</span></code></pre></div>

**Variáveis especiais:**
- `$0` - Linha inteira
- `$1, $2, ...` - Colunas 1, 2, ...
- `NR` - Número da linha
- `NF` - Número de campos

**Exemplos:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-ecrk3ngtt" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Imprimir primeira coluna</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">awk</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;{print $1}&#x27;</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Imprimir primeira linha</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">awk</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;NR==1&#x27;</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Imprimir última linha</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">awk</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;END {print}&#x27;</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Filtrar por valor</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">awk</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;$3 &gt; 100&#x27;</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Somar valores de coluna</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">awk</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;{sum+=$2} END {print sum}&#x27;</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Com delimitador customizado</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">awk</span><span> -F</span><span class="token" style="color:rgb(173, 219, 103)">&#x27;:&#x27;</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;{print $1}&#x27;</span><span> /etc/passwd
</span></code></pre></div>

---

## 📊 Processamento de Texto

### cut

**Descrição:** Extrai seções de linhas.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-idiwr9hsp" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Extrair primeira coluna (delimitador espaço)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">cut</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-d</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot; &quot;</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-f1</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Extrair colunas 1 e 3</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">cut</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-d</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot; &quot;</span><span> -f1,3 arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Extrair caracteres 1-10</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">cut</span><span> -c1-10 arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Extrair do /etc/passwd</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">cut</span><span> -d: -f1,6 /etc/passwd
</span></code></pre></div>

---

### sort

**Descrição:** Ordena linhas.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-8cllrqqef" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ordenar alfabeticamente</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sort</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ordenar numericamente</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sort</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-n</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ordenar reverso</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sort</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-r</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ordenar por coluna 2</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sort</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-k2</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ordenar e remover duplicatas</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sort</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-u</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ordenar por mês</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sort</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-M</span><span> arquivo.txt
</span></code></pre></div>

---

### uniq

**Descrição:** Remove linhas duplicadas adjacentes.

**⚠️ Requer `sort` antes!**

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-45ggle685" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Remover duplicatas</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sort</span><span> arquivo.txt </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">uniq</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Contar ocorrências</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sort</span><span> arquivo.txt </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">uniq</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-c</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Mostrar apenas duplicatas</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sort</span><span> arquivo.txt </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">uniq</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-d</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Mostrar apenas únicas</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sort</span><span> arquivo.txt </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">uniq</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-u</span><span>
</span></code></pre></div>

---

### wc (Word Count)

**Descrição:** Conta linhas, palavras e caracteres.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-50xkofdec" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Contar linhas</span><span>
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

---

### tr (Translate)

**Descrição:** Traduz ou deleta caracteres.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-eo3g22z3n" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Converter minúsculas para maiúsculas</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">cat</span><span> arquivo.txt </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">tr</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;a-z&#x27;</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;A-Z&#x27;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Deletar caracteres</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">cat</span><span> arquivo.txt </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">tr</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-d</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;0-9&#x27;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Substituir espaços por underscores</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">cat</span><span> arquivo.txt </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">tr</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27; &#x27;</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;_&#x27;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Remover quebras de linha</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">cat</span><span> arquivo.txt </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">tr</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-d</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;\n&#x27;</span><span>
</span></code></pre></div>

---

## 📦 Compactação e Arquivamento

### tar (Tape Archive)

**Descrição:** Arquivador de arquivos.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-1ml7qf3pa" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Criar arquivo tar</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">tar</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-cf</span><span> arquivo.tar diretorio/
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Criar arquivo tar.gz (compactado)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">tar</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-czf</span><span> arquivo.tar.gz diretorio/
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Criar arquivo tar.bz2 (mais compactado)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">tar</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-cjf</span><span> arquivo.tar.bz2 diretorio/
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Extrair tar</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">tar</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-xf</span><span> arquivo.tar
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Extrair tar.gz</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">tar</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-xzf</span><span> arquivo.tar.gz
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Extrair para diretório específico</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">tar</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-xzf</span><span> arquivo.tar.gz </span><span class="token parameter" style="color:rgb(214, 222, 235)">-C</span><span> /destino/
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Listar conteúdo sem extrair</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">tar</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-tzf</span><span> arquivo.tar.gz
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Extrair arquivo específico</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">tar</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-xzf</span><span> arquivo.tar.gz caminho/arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verbose (mostrar progresso)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">tar</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-xzvf</span><span> arquivo.tar.gz
</span></code></pre></div>

**Flags:**
- `c` - Create (criar)
- `x` - Extract (extrair)
- `t` - List (listar)
- `z` - gzip
- `j` - bzip2
- `v` - Verbose
- `f` - File

---

### gzip

**Descrição:** Compactador (substitui arquivo original).

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-ng35zc5l1" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Compactar</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">gzip</span><span> arquivo.txt
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Gera: arquivo.txt.gz</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Descompactar</span><span>
</span>gunzip arquivo.txt.gz
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Compactar mantendo original</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">gzip</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-k</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Compactar com máxima compressão</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">gzip</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-9</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ver conteúdo sem descompactar</span><span>
</span>zcat arquivo.txt.gz
<!-- -->zless arquivo.txt.gz
</code></pre></div>

---

### bzip2

**Descrição:** Compactador (mais eficiente que gzip).

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-hotcewhm3" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Compactar</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">bzip2</span><span> arquivo.txt
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Gera: arquivo.txt.bz2</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Descompactar</span><span>
</span>bunzip2 arquivo.txt.bz2
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ou</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">bzip2</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-d</span><span> arquivo.txt.bz2
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ver conteúdo</span><span>
</span>bzcat arquivo.txt.bz2
<!-- -->bzless arquivo.txt.bz2
</code></pre></div>

---

### zip/unzip

**Descrição:** Compactador compatível com Windows.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-69qdr4vt7" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Instalar (se necessário)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">apt</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">install</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">zip</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">unzip</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Compactar arquivo</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">zip</span><span> arquivo.zip arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Compactar diretório</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">zip</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-r</span><span> diretorio.zip diretorio/
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Descompactar</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">unzip</span><span> arquivo.zip
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Descompactar para diretório específico</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">unzip</span><span> arquivo.zip </span><span class="token parameter" style="color:rgb(214, 222, 235)">-d</span><span> /destino/
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Listar conteúdo</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">unzip</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-l</span><span> arquivo.zip
</span></code></pre></div>

---

### rar

**Descrição:** Compactador RAR (requer instalação).

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-3qv6spdev" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Instalar</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">apt</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">install</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">rar</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">unrar</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Compactar</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">rar</span><span> a arquivo.rar arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Descompactar</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">rar</span><span> x arquivo.rar
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ou</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">unrar</span><span> x arquivo.rar
</span></code></pre></div>

---

## 🔗 Links Relacionados

- [[03_Comandos-Basicos]]
- [[05_Permissoes-Linux]]
- [[23_Bash-Scripting]]
- [[24_AWK-Avancado]]

---

## 📚 Referências

- GNU Coreutils: [gnu.org/software/coreutils](https://www.gnu.org/software/coreutils/)
- Sed Manual: [gnu.org/software/sed/manual](https://www.gnu.org/software/sed/manual/)
- AWK Manual: [gnu.org/software/gawk/manual](https://www.gnu.org/software/gawk/manual/)
