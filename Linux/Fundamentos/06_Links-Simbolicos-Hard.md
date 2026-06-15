
# 🔗 Links Simbólicos e Hard Links no Linux

> **Tags:** #linux #links #simbolico #hard-link #inode #filesystem

---

## 📌 Visão Geral

No Linux, links são atalhos para arquivos ou diretórios, mas com comportamentos distintos.

🎯 **Objetivo:** Entender a diferença entre links simbólicos e hard links e como usá-los.

---

## 🔗 Links Simbólicos (Soft Links)

**Descrição:** Um ponteiro para outro arquivo ou diretório. Funciona como um atalho.

**Características:**
- ✅ Pode apontar para **arquivos ou diretórios**.
- ✅ Pode apontar para arquivos em **outras partições** ou sistemas de arquivos.
- ✅ Possui um **inode diferente** do arquivo original.
- ✅ Se o arquivo original for deletado, o link simbólico se torna **quebrado (dangling link)**.
- ✅ O `ls -l` mostra um `l` no tipo de arquivo e aponta para o original.

**Sintaxe:** `ln -s <caminho_original> <caminho_do_link>`

---

### Exemplos

bash

#### Criar arquivo original

echo "Conteúdo do arquivo original" > original.txt
#### Criar link simbólico para arquivo

ln -s original.txt link_simbolico.txt
#### Criar link simbólico para diretório

mkdir pasta_original ln -s pasta_original link_pasta_simbolica

# Verificar

ls -l

```
**Output:**

lrwxrwxrwx 1 usuario grupo 12 Jan 3 10:00 link_simbolico.txt -> original.txt lrwxrwxrwx 1 usuario grupo 14 Jan 3 10:00 link_pasta_simbolica -> pasta_original/ -rw-r--r-- 1 usuario grupo 26 Jan 3 10:00 original.txt drwxr-xr-x 2 usuario grupo 4096 Jan 3 10:00 pasta_original/

```


---

### Comportamento

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-apmsubm97" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ler o link simbólico (lê o original)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">cat</span><span> link_simbolico.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Deletar o link simbólico (original permanece)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">rm</span><span> link_simbolico.txt
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">ls</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-l</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Deletar o arquivo original (link simbólico quebra)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">rm</span><span> original.txt
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">ls</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-l</span><span>
</span></code></pre></div>

**Output após deletar original:**
```

lrwxrwxrwx 1 usuario grupo 12 Jan 3 10:00 link_simbolico.txt -> original.txt # Link quebrado (vermelho no terminal)

```
---

## ⛓️ Hard Links

**Descrição:** Uma entrada de diretório adicional para um arquivo existente. É como ter **múltiplos nomes para o mesmo arquivo**.

**Características:**
- ✅ Só pode apontar para **arquivos** (não diretórios).
- ✅ Só pode apontar para arquivos na **mesma partição** ou sistema de arquivos.
- ✅ Compartilha o **mesmo inode** com o arquivo original.
- ✅ Se o arquivo original for deletado, o hard link **continua existindo** e o conteúdo permanece acessível (o arquivo só é realmente deletado quando todas as referências a ele são removidas).
- ✅ O `ls -l` mostra o mesmo tipo de arquivo e o contador de links aumenta.

**Sintaxe:** `ln <caminho_original> <caminho_do_link>`

---

### Exemplos

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-2si3dp75u" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Criar arquivo original</span><span>
</span><span></span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Conteúdo do arquivo original&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">&gt;</span><span> original_hard.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Criar hard link</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">ln</span><span> original_hard.txt hard_link.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar (mesmo inode, contador de links = 2)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">ls</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-li</span><span>
</span></code></pre></div>

**Output:**
```

123456 -rw-r--r-- 2 usuario grupo 26 Jan 3 10:00 hard_link.txt 123456 -rw-r--r-- 2 usuario grupo 26 Jan 3 10:00 original_hard.txt

```
---

### Comportamento

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-oat30rh6p" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ler o hard link (lê o mesmo conteúdo)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">cat</span><span> hard_link.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Deletar o hard link (original permanece, contador de links diminui)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">rm</span><span> hard_link.txt
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">ls</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-li</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Deletar o arquivo original (hard link permanece e o conteúdo é acessível)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">rm</span><span> original_hard.txt
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">ls</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-li</span><span>
</span></code></pre></div>

**Output após deletar original:**
```

123456 -rw-r--r-- 1 usuario grupo 26 Jan 3 10:00 hard_link.txt # Arquivo ainda existe e é acessível

```
---

## 🆚 Comparação

| Característica        | Link Simbólico (Soft Link)        | Hard Link                             |
| --------------------- | --------------------------------- | ------------------------------------- |
| **Tipo**              | Atalho/Ponteiro                   | Entrada de diretório adicional        |
| **Inode**             | Diferente do original             | Mesmo do original                     |
| **Partição**          | Pode ser diferente                | Deve ser a mesma                      |
| **Diretórios**        | Sim                               | Não (apenas arquivos)                 |
| **Original Deletado** | Quebra (dangling)                 | Permanece acessível                   |
| **\`ls -l\`**         | `l` no tipo, aponta para original | Mesmo tipo, contador de links aumenta |

---

## 🔢 Inodes

**Descrição:** Um **inode** é uma estrutura de dados em sistemas de arquivos Unix-like que armazena informações sobre um arquivo ou diretório, exceto o nome e o conteúdo.

**Informações no Inode:**
- Tipo de arquivo
- Permissões
- Proprietário e grupo
- Timestamps (criação, modificação, acesso)
- Tamanho do arquivo
- Número de hard links
- Ponteiros para os blocos de dados no disco

**Visualizar Inode:** `ls -i`

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-pbav97hu1" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">ls</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-i</span><span> original.txt link_simbolico.txt hard_link.txt
</span></code></pre></div>

**Output:**
```

123456 original.txt 789012 link_simbolico.txt 123456 hard_link.txt

```
(Note que `original.txt` e `hard_link.txt` têm o mesmo inode `123456`, enquanto `link_simbolico.txt` tem um inode diferente `789012`).

---

## 🔗 Links Relacionados

- [[03_Comandos-Basicos]]
- [[04_Gerenciamento-de-Arquivos]]
- [[05_Permissoes-Linux]]
- [[10_Gerenciamento-de-Discos]]

---

## 📚 Referências

- Linux Command Line: [linuxcommand.org/lc3_lts0090.php](http://linuxcommand.org/lc3_lts0090.php)
- Inode (Wikipedia): [en.wikipedia.org/wiki/Inode](https://en.wikipedia.org/wiki/Inode)