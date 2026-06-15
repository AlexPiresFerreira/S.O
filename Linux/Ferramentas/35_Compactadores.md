
# 📦 Compactadores e Arquivadores no Linux

> **Tags:** #linux #compactacao #arquivamento #tar #gzip #bzip2 #zip #rar

---

## 📌 Visão Geral

Ferramentas de compactação e arquivamento são essenciais para economizar espaço em disco, otimizar transferências de rede e organizar backups.

🎯 **Objetivo:** Utilizar as principais ferramentas para compactar, descompactar e arquivar arquivos e diretórios.

---

## 📊 Conceitos

### Arquivamento

**Descrição:** Combinar múltiplos arquivos e diretórios em um único arquivo (sem compactação).

**Ferramenta principal:** `tar`

---

### Compactação (Compressão)

**Descrição:** Reduzir o tamanho de um arquivo ou de um arquivo arquivado.

**Ferramentas principais:** `gzip`, `bzip2`, `xz`

---

## 📦 Arquivador: tar (Tape Archive)

**Descrição:** Ferramenta versátil para criar e extrair arquivos `.tar`. Pode ser combinado com compactadores.

**Sintaxe:** `tar [opções] <arquivo_saida> <arquivos/diretorios_entrada>`

### Opções Comuns

| Opção | Descrição |
|-------|-----------|
| `-c` | **Create:** Criar um novo arquivo `tar`. |
| `-x` | **Extract:** Extrair arquivos de um `tar`. |
| `-t` | **List:** Listar o conteúdo de um `tar`. |
| `-f <file>` | **File:** Especificar o nome do arquivo `tar`. |
| `-v` | **Verbose:** Exibir o progresso detalhado. |
| `-z` | **Gzip:** Usar `gzip` para compactar/descompactar (`.tar.gz` ou `.tgz`). |
| `-j` | **Bzip2:** Usar `bzip2` para compactar/descompactar (`.tar.bz2` ou `.tbz`). |
| `-J` | **Xz:** Usar `xz` para compactar/descompactar (`.tar.xz` ou `.txz`). |
| `-C <dir>` | **Change Directory:** Mudar para um diretório antes de extrair. |
| `--exclude=<pattern>` | Excluir arquivos/diretórios que correspondem ao padrão. |

---

### Exemplos

#### Criar Arquivo Tar

bash
#### Criar arquivo .tar (sem compactação)

tar -cvf meu_backup.tar /home/usuario/documentos
#### Criar arquivo .tar.gz (com gzip)

tar -czvf meu_backup.tar.gz /home/usuario/documentos
#### Criar arquivo .tar.bz2 (com bzip2)

tar -cjvf meu_backup.tar.bz2 /home/usuario/documentos
#### Criar arquivo .tar.xz (com xz)

tar -cJvf meu_backup.tar.xz /home/usuario/documentos
#### Criar .tar.gz excluindo um diretório

tar -czvf meu_backup_excl.tar.gz /home/usuario/documentos --exclude=/home/usuario/documentos/temp


---

#### Extrair Arquivo Tar

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-qdacvcbta" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Extrair .tar (no diretório atual)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">tar</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-xvf</span><span> meu_backup.tar
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Extrair .tar.gz</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">tar</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-xzvf</span><span> meu_backup.tar.gz
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Extrair .tar.bz2</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">tar</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-xjvf</span><span> meu_backup.tar.bz2
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Extrair .tar.xz</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">tar</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-xJvf</span><span> meu_backup.tar.xz
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Extrair para um diretório específico</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">tar</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-xzvf</span><span> meu_backup.tar.gz </span><span class="token parameter" style="color:rgb(214, 222, 235)">-C</span><span> /tmp/restauracao
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Extrair um único arquivo de um tar.gz</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">tar</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-xzvf</span><span> meu_backup.tar.gz caminho/para/arquivo_especifico.txt
</span></code></pre></div>

---

#### Listar Conteúdo de Arquivo Tar

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-emflo5x0u" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Listar conteúdo de .tar.gz</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">tar</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-tzvf</span><span> meu_backup.tar.gz
</span></code></pre></div>

---

## 🗜️ Compactadores Individuais

### 1. gzip

**Descrição:** Compacta arquivos individualmente, geralmente substituindo o original por um `.gz`.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-keegctf35" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Compactar arquivo (substitui original)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">gzip</span><span> arquivo.txt
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Gera: arquivo.txt.gz</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Descompactar arquivo</span><span>
</span>gunzip arquivo.txt.gz
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ou</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">gzip</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-d</span><span> arquivo.txt.gz
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Compactar mantendo o original</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">gzip</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-k</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Compactar com nível máximo (9)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">gzip</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-9</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ver conteúdo de arquivo .gz sem descompactar</span><span>
</span>zcat arquivo.txt.gz
<!-- -->zless arquivo.txt.gz
</code></pre></div>

---

### 2. bzip2

**Descrição:** Compacta arquivos individualmente, geralmente substituindo o original por um `.bz2`. Mais eficiente que `gzip`.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-bfo9vxm9m" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Compactar arquivo</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">bzip2</span><span> arquivo.txt
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Gera: arquivo.txt.bz2</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Descompactar arquivo</span><span>
</span>bunzip2 arquivo.txt.bz2
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ou</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">bzip2</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-d</span><span> arquivo.txt.bz2
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Compactar mantendo o original</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">bzip2</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-k</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ver conteúdo de arquivo .bz2 sem descompactar</span><span>
</span>bzcat arquivo.txt.bz2
<!-- -->bzless arquivo.txt.bz2
</code></pre></div>

---

### 3. xz

**Descrição:** Compacta arquivos individualmente, geralmente substituindo o original por um `.xz`. Mais eficiente que `gzip` e `bzip2`.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-blqr53njx" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Compactar arquivo</span><span>
</span>xz arquivo.txt
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Gera: arquivo.txt.xz</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Descompactar arquivo</span><span>
</span>unxz arquivo.txt.xz
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ou</span><span>
</span><span>xz </span><span class="token parameter" style="color:rgb(214, 222, 235)">-d</span><span> arquivo.txt.xz
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Compactar mantendo o original</span><span>
</span><span>xz </span><span class="token parameter" style="color:rgb(214, 222, 235)">-k</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ver conteúdo de arquivo .xz sem descompactar</span><span>
</span>xzcat arquivo.txt.xz
<!-- -->xzless arquivo.txt.xz
</code></pre></div>

---

## 🗂️ Compatibilidade com Windows: zip / unzip

**Descrição:** Ferramentas para criar e extrair arquivos `.zip`, compatíveis com Windows.

**Instalação (se necessário):**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-z4xa665w1" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">apt</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">install</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">zip</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">unzip</span><span>
</span></code></pre></div>

### Exemplos

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-2a3hjshza" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Compactar arquivo</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">zip</span><span> meu_arquivo.zip arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Compactar diretório (recursivo)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">zip</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-r</span><span> meu_diretorio.zip meu_diretorio/
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Descompactar arquivo</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">unzip</span><span> meu_arquivo.zip
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Descompactar para diretório específico</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">unzip</span><span> meu_arquivo.zip </span><span class="token parameter" style="color:rgb(214, 222, 235)">-d</span><span> /tmp/extraido
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Listar conteúdo sem extrair</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">unzip</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-l</span><span> meu_arquivo.zip
</span></code></pre></div>

---

## 🔒 Arquivos RAR

**Descrição:** Formato proprietário de compactação. Requer ferramentas específicas.

**Instalação:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-xbsjdi34x" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">apt</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">install</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">rar</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">unrar</span><span>
</span></code></pre></div>

### Exemplos

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-71kstn8e9" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Compactar arquivo</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">rar</span><span> a meu_arquivo.rar arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Compactar diretório</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">rar</span><span> a </span><span class="token parameter" style="color:rgb(214, 222, 235)">-r</span><span> meu_diretorio.rar meu_diretorio/
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Descompactar arquivo</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">unrar</span><span> x meu_arquivo.rar
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ou</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">rar</span><span> x meu_arquivo.rar
</span></code></pre></div>

---

## 🔗 Links Relacionados

- [[04_Gerenciamento-de-Arquivos]]
- [[23_Bash-Scripting]]
- [[13_Cron-e-Agendamento]]

---

## 📚 Referências

- Tar Man Page: [man7.org/linux/man-pages/man1/tar.1.html](https://man7.org/linux/man-pages/man1/tar.1.html)
- Gzip Man Page: [man7.org/linux/man-pages/man1/gzip.1.html](https://man7.org/linux/man-pages/man1/gzip.1.html)
- Bzip2 Man Page: [man7.org/linux/man-pages/man1/bzip2.1.html](https://man7.org/linux/man-pages/man1/bzip2.1.html)
- Xz Man Page: [man7.org/linux/man-pages/man1/xz.1.html](https://man7.org/linux/man-pages/man1/xz.1.html)
- Zip Man Page: [man7.org/linux/man-pages/man1/zip.1.html](https://man7.org/linux/man-pages/man1/zip.1.html)
