
# 🔐 Permissões no Linux

> **Tags:** #linux #permissoes #chmod #chown #suid #sgid #sticky-bit #acl

---

## 📌 Visão Geral

O Linux usa um sistema de permissões para controlar quem pode **ler**, **escrever** e **executar** arquivos e diretórios.

🎯 **Objetivo:** Entender e gerenciar permissões para segurança e controle de acesso.

---

## 👥 Tipos de Usuários

| Tipo | Símbolo | Descrição |
|------|---------|-----------|
| **Proprietário (User)** | `u` | Dono do arquivo |
| **Grupo (Group)** | `g` | Grupo que possui o arquivo |
| **Outros (Others)** | `o` | Todos os outros usuários |
| **Todos (All)** | `a` | User + Group + Others |

---

## 📊 Tipos de Permissões

| Permissão | Símbolo | Valor Octal | Descrição |
|-----------|---------|-------------|-----------|
| **Leitura (Read)** | `r` | 4 | Ler conteúdo do arquivo / Listar diretório |
| **Escrita (Write)** | `w` | 2 | Modificar arquivo / Criar/deletar arquivos no diretório |
| **Execução (Execute)** | `x` | 1 | Executar arquivo / Acessar diretório |
| **Nenhuma** | `-` | 0 | Sem permissão |

---

## 🔍 Visualizando Permissões

```

bash ls -l arquivo.txt

```
**Output:**
```

-rw-r--r-- 1 usuario grupo 1234 Jan 03 10:30 arquivo.txt │││││││││ │││││││││ │││└┴┴┴┴┴─ Permissões (9 caracteres) ││└─────── Número de links │└──────── Proprietário └───────── Tipo de arquivo

```
---

### Estrutura de Permissões
```

-rw-r--r-- │└┬┘└┬┘└┬┘ │ │ │ └─ Outros (r--) │ │ └──── Grupo (r--) │ └─────── Proprietário (rw-) └───────── Tipo de arquivo

```
**Tipo de arquivo:**
- `-` - Arquivo regular
- `d` - Diretório
- `l` - Link simbólico
- `c` - Dispositivo de caractere
- `b` - Dispositivo de bloco
- `s` - Socket
- `p` - Pipe

---

## 🔧 Alterando Permissões (chmod)

### Modo Simbólico

**Sintaxe:** `chmod [quem][operação][permissão] arquivo`

**Quem:**
- `u` - User (proprietário)
- `g` - Group
- `o` - Others
- `a` - All

**Operação:**
- `+` - Adicionar permissão
- `-` - Remover permissão
- `=` - Definir permissão exata

**Exemplos:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-0268e9f7a" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Adicionar execução para proprietário</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">chmod</span><span> u+x script.sh
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Remover escrita para grupo</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">chmod</span><span> g-w arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Adicionar leitura para todos</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">chmod</span><span> a+r arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Definir permissão exata para proprietário</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">chmod</span><span> </span><span class="token assign-left" style="color:rgb(214, 222, 235)">u</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span>rwx arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Múltiplas alterações</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">chmod</span><span> u+x,g-w,o-r arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Todos podem ler e executar</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">chmod</span><span> a+rx script.sh
</span></code></pre></div>

---

### Modo Octal (Numérico)

**Cálculo:**
- `r` = 4
- `w` = 2
- `x` = 1

**Soma dos valores:**
- `rwx` = 4+2+1 = 7
- `rw-` = 4+2+0 = 6
- `r-x` = 4+0+1 = 5
- `r--` = 4+0+0 = 4
- `---` = 0+0+0 = 0

**Sintaxe:** `chmod [proprietário][grupo][outros] arquivo`

**Exemplos:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-49y7gfufe" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># rwxr-xr-x (755)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">chmod</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">755</span><span> script.sh
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># rw-r--r-- (644)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">chmod</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">644</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># rwx------ (700)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">chmod</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">700</span><span> script_privado.sh
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># rw-rw-r-- (664)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">chmod</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">664</span><span> documento.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># rwxrwxrwx (777) - PERIGOSO! Todos podem tudo</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">chmod</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">777</span><span> arquivo.txt
</span></code></pre></div>

---

### Permissões Comuns

| Octal | Simbólico | Uso Típico |
|-------|-----------|------------|
| **755** | `rwxr-xr-x` | Scripts, executáveis |
| **644** | `rw-r--r--` | Arquivos de texto, documentos |
| **600** | `rw-------` | Arquivos privados (senhas, chaves SSH) |
| **700** | `rwx------` | Diretórios privados |
| **775** | `rwxrwxr-x` | Diretórios compartilhados |
| **666** | `rw-rw-rw-` | Arquivos temporários (evitar) |
| **777** | `rwxrwxrwx` | ⚠️ Perigoso! Evitar |

---

### Recursivo

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-xhabsfbq6" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Alterar permissões recursivamente</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">chmod</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-R</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">755</span><span> diretorio/
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Alterar apenas diretórios</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">find</span><span> diretorio/ </span><span class="token parameter" style="color:rgb(214, 222, 235)">-type</span><span> d </span><span class="token parameter" style="color:rgb(214, 222, 235)">-exec</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">chmod</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">755</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">{</span><span class="token" style="color:rgb(199, 146, 234)">}</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">\</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Alterar apenas arquivos</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">find</span><span> diretorio/ </span><span class="token parameter" style="color:rgb(214, 222, 235)">-type</span><span> f </span><span class="token parameter" style="color:rgb(214, 222, 235)">-exec</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">chmod</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">644</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">{</span><span class="token" style="color:rgb(199, 146, 234)">}</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">\</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span></code></pre></div>

---

## 👤 Alterando Proprietário (chown)

**Sintaxe:** `chown [proprietário]:[grupo] arquivo`

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-av98gic5p" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Alterar proprietário</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">chown</span><span> usuario arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Alterar proprietário e grupo</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">chown</span><span> usuario:grupo arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Alterar apenas grupo</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">chown</span><span> :grupo arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Recursivo</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">chown</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-R</span><span> usuario:grupo diretorio/
</span></code></pre></div>

---

## 👥 Alterando Grupo (chgrp)

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-pxvri4kuu" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Alterar grupo</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">chgrp</span><span> grupo arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Recursivo</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">chgrp</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-R</span><span> grupo diretorio/
</span></code></pre></div>

---

## 🔒 Permissões Especiais

### SUID (Set User ID)

**Descrição:** Executa arquivo com permissões do **proprietário** (não do usuário que executa).

**Valor octal:** 4

**Uso:** Permitir que usuários comuns executem comandos que requerem root.

**Exemplo:** `/usr/bin/passwd`

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-0wqn1ozdt" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Adicionar SUID</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">chmod</span><span> u+s arquivo
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">chmod</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">4755</span><span> arquivo
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">ls</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-l</span><span> arquivo
</span><span>-rwsr-xr-x  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># &#x27;s&#x27; no lugar de &#x27;x&#x27;</span><span>
</span></code></pre></div>

**⚠️ Perigo:** Arquivos SUID podem ser explorados para escalação de privilégios!

---

### SGID (Set Group ID)

**Descrição:** 
- **Arquivo:** Executa com permissões do **grupo**
- **Diretório:** Novos arquivos herdam o **grupo do diretório**

**Valor octal:** 2

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-znxg0aqya" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Adicionar SGID</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">chmod</span><span> g+s arquivo
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">chmod</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">2755</span><span> arquivo
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">ls</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-l</span><span> arquivo
</span><span>-rwxr-sr-x  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># &#x27;s&#x27; no lugar de &#x27;x&#x27;</span><span>
</span></code></pre></div>

---

### Sticky Bit

**Descrição:** Em diretórios, apenas o **proprietário** pode deletar seus próprios arquivos.

**Valor octal:** 1

**Uso:** Diretórios compartilhados (ex: `/tmp`)

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-hr5gyygfm" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Adicionar Sticky Bit</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">chmod</span><span> +t diretorio/
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">chmod</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">1777</span><span> diretorio/
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">ls</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-ld</span><span> diretorio/
</span><span>drwxrwxrwt  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># &#x27;t&#x27; no lugar de &#x27;x&#x27;</span><span>
</span></code></pre></div>

**Exemplo:** `/tmp/`
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-v744rfudl" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">ls</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-ld</span><span> /tmp
</span>drwxrwxrwt
</code></pre></div>

---

### Combinando Permissões Especiais

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-b612fyhtg" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># SUID + permissões normais</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">chmod</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">4755</span><span> arquivo  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># rwsr-xr-x</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># SGID + permissões normais</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">chmod</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">2755</span><span> arquivo  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># rwxr-sr-x</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Sticky Bit + permissões normais</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">chmod</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">1777</span><span> diretorio/  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># rwxrwxrwt</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># SUID + SGID</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">chmod</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">6755</span><span> arquivo  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># rwsr-sr-x</span><span>
</span></code></pre></div>

---

## 🎯 Permissões em Diretórios

| Permissão | Efeito |
|-----------|--------|
| **r (read)** | Listar conteúdo (`ls`) |
| **w (write)** | Criar/deletar arquivos (requer `x` também) |
| **x (execute)** | Acessar diretório (`cd`) |

**Exemplos:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-bww5vp0i9" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Diretório sem &#x27;x&#x27; - não consegue acessar</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">chmod</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">644</span><span> diretorio/
</span><span></span><span class="token" style="color:rgb(255, 203, 139)">cd</span><span> diretorio/  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Erro: Permission denied</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Diretório com &#x27;x&#x27; mas sem &#x27;r&#x27; - pode acessar mas não listar</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">chmod</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">311</span><span> diretorio/
</span><span></span><span class="token" style="color:rgb(255, 203, 139)">cd</span><span> diretorio/  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># OK</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">ls</span><span>  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Erro: Permission denied</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Diretório com &#x27;w&#x27; mas sem &#x27;x&#x27; - não consegue criar arquivos</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">chmod</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">622</span><span> diretorio/
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">touch</span><span> diretorio/arquivo.txt  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Erro: Permission denied</span><span>
</span></code></pre></div>

---

## 🔗 Links Relacionados

- [[03_Comandos-Basicos]]
- [[07_Gerenciamento-de-Usuarios]]
- [[20_ACL]]
- [[19_Hardening-Linux]]

---

## 📚 Referências

- Chmod Manual: [man7.org/linux/man-pages/man1/chmod.1.html](https://man7.org/linux/man-pages/man1/chmod.1.html)
- Linux Permissions: [linuxcommand.org/lc3_lts0090.php](http://linuxcommand.org/lc3_lts0090.php)