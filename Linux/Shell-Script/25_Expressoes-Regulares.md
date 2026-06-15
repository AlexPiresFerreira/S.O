
# 📝 Expressões Regulares (Regex) no Linux

> **Tags:** #linux #regex #grep #sed #awk #shell-script #text-processing

---

## 📌 Visão Geral

**Expressões Regulares (Regex)** são sequências de caracteres que definem um padrão de busca.

🎯 **Objetivo:** Filtrar, extrair e manipular texto de forma poderosa e flexível.

---

## 📊 Caracteres Regex Básicos

| Caractere | Significado | Exemplo | Corresponde a |
|-----------|-------------|---------|---------------|
| `.` | Qualquer caractere único (exceto nova linha) | `a.c` | `abc`, `adc`, `a1c` |
| `[ ]` | Qualquer caractere especificado dentro da lista | `[aeiou]` | `a`, `e`, `i`, `o`, `u` |
| `[^ ]` | Não é o caractere especificado dentro da lista | `[^0-9]` | Qualquer caractere que não seja um dígito |
| `*` | Zero ou mais ocorrências do caractere/grupo anterior | `a*b` | `b`, `ab`, `aab`, `aaab` |
| `^` | Início da linha | `^erro` | Linhas que começam com "erro" |
| `$` | Fim da linha | `log$` | Linhas que terminam com "log" |
| `\` | Caractere de escape (para usar caracteres especiais como literais) | `\.` | O caractere literal `.` |

---

### Exemplos de Listas `[]`

- `[0-9]`: Qualquer dígito de 0 a 9.
- `[a-z]`: Qualquer letra minúscula.
- `[A-Z]`: Qualquer letra maiúscula.
- `[a-zA-Z]`: Qualquer letra.
- `[a-zA-Z0-9]`: Qualquer letra ou dígito.
- `[[:digit:]]`: Equivalente a `[0-9]`.
- `[[:alpha:]]`: Equivalente a `[a-zA-Z]`.
- `[[:alnum:]]`: Equivalente a `[a-zA-Z0-9]`.
- `[[:space:]]`: Espaço em branco.

---

## 🚀 Caracteres Regex Estendidos (egrep ou grep -E)

| Caractere | Significado | Exemplo | Corresponde a |
|-----------|-------------|---------|---------------|
| `+` | Uma ou mais ocorrências do caractere/grupo anterior | `a+b` | `ab`, `aab`, `aaab` (mas não `b`) |
| `?` | Zero ou uma ocorrência do caractere/grupo anterior (opcional) | `colou?r` | `color`, `colour` |
| `{n}` | Exatamente `n` ocorrências | `a{3}` | `aaa` |
| `{n,}` | `n` ou mais ocorrências | `a{2,}` | `aa`, `aaa`, `aaaa` |
| `{n,m}` | Entre `n` e `m` ocorrências | `a{2,4}` | `aa`, `aaa`, `aaaa` |
| `|` | Alternação (OU lógico) | `cat|dog` | `cat` ou `dog` |
| `( )` | Agrupamento (para aplicar operadores a um grupo) | `(ab)+` | `ab`, `abab`, `ababab` |

---

## 🛠️ Ferramentas Linux com Regex

### 1. grep (Global Regular Expression Print)

**Descrição:** Busca padrões em arquivos.

**Sintaxe:** `grep [opções] <pattern> <arquivo>`

**Opções importantes para Regex:**
- `-E` ou `egrep`: Usar Regex estendidas.
- `-P`: Usar Regex compatíveis com Perl (PCRE - mais poderosas).
- `-i`: Ignorar case.
- `-v`: Inverter busca (linhas que NÃO contêm o padrão).
- `-n`: Mostrar número da linha.
- `-r`: Busca recursiva em diretórios.

**Exemplos:**

bash
#### Linhas que começam com "ERROR"

grep "^ERROR" log.txt
#### Linhas que contêm "WARNING" ou "ERROR"

grep -E "WARNING|ERROR" log.txt
#### Linhas que contêm um IP (ex: 192.168.1.10)

grep -E "\b([0-9]{1,3}.){3}[0-9]{1,3}\b" access.log
#### Linhas que contêm "user" seguido de 1 ou mais dígitos

grep -E "user[0-9]+" /etc/passwd
#### Linhas que não contêm comentários (começam com #)

grep -v "^#" arquivo.conf

---

### 2. sed (Stream Editor)

**Descrição:** Editor de texto em stream, muito usado para substituições com Regex.

**Sintaxe:** `sed 's/<pattern>/<replacement>/[flags]' <arquivo>`

**Flags comuns:**
- `g`: Global (substituir todas as ocorrências na linha).
- `i`: Ignorar case.
- `p`: Imprimir a linha (usar com `-n`).

**Exemplos:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-dr4oj3mja" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Substituir todas as ocorrências de &quot;erro&quot; por &quot;ERRO&quot;</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sed</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;s/erro/ERRO/g&#x27;</span><span> log.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Substituir IPs (192.168.x.x) por &quot;[IP_PRIVADO]&quot;</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sed</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-E</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;s/192\.168\.[0-9]{1,3}\.[0-9]{1,3}/[IP_PRIVADO]/g&#x27;</span><span> access.log
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Deletar linhas vazias</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sed</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;/^$/d&#x27;</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Deletar linhas que começam com &#x27;#&#x27;</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sed</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;/^#/d&#x27;</span><span> arquivo.conf
</span></code></pre></div>

---

### 3. awk (Aho, Weinberger, Kernighan)

**Descrição:** Linguagem de processamento de texto que usa Regex em seus padrões.

**Sintaxe:** `awk '/pattern/ { action }' <arquivo>`

**Exemplos:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-h2pbovuh5" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Imprimir linhas que contêm &quot;ERROR&quot;</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">awk</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;/ERROR/ {print}&#x27;</span><span> log.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Imprimir linhas onde a primeira coluna começa com &quot;GET&quot;</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">awk</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;$1 ~ /^GET/ {print}&#x27;</span><span> access.log
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Imprimir linhas onde a segunda coluna NÃO contém &quot;admin&quot;</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">awk</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;$2 !~ /admin/ {print}&#x27;</span><span> usuarios.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Substituir IPs por &quot;[IP_ANONIMO]&quot; na primeira coluna</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">awk</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;{gsub(/([0-9]{1,3}\.){3}[0-9]{1,3}/, &quot;[IP_ANONIMO]&quot;, $1); print}&#x27;</span><span> access.log
</span></code></pre></div>

---

## 🎯 Exemplos de Regex para Segurança

### 1. IPs

- **IPv4:** `\b([0-9]{1,3}\.){3}[0-9]{1,3}\b`
- **IPv6 (simplificado):** `([0-9a-fA-F]{1,4}:){7}[0-9a-fA-F]{1,4}`

---

### 2. URLs

- `https?:\/\/(www\.)?[-a-zA-Z0-9@:%._\+~#=]{1,256}\.[a-zA-Z0-9()]{1,6}\b([-a-zA-Z0-9()@:%_\+.~#?&//=]*)`

---

### 3. Endereços de Email

- `[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}`

---

### 4. Senhas (Exemplo de validação)

- `^(?=.*[a-z])(?=.*[A-Z])(?=.*[0-9])(?=.*[!@#$%^&*])(?=.{8,})`
  - Pelo menos 1 minúscula, 1 maiúscula, 1 dígito, 1 símbolo, 8+ caracteres.

---

### 5. Datas (Formato YYYY-MM-DD)

- `[0-9]{4}-[0-9]{2}-[0-9]{2}`

---

## 🔗 Links Relacionados

- [[23_Bash-Scripting]]
- [[24_AWK-Avancado]]
- [[04_Gerenciamento-de-Arquivos]]
- [[22_Auditoria-e-Logs]]

---

## 📚 Referências

- Regex101 (testador de Regex): [regex101.com](https://regex101.com/)
- Regex Tutorial: [www.regular-expressions.info](https://www.regular-expressions.info/)
- Grep Man Page: [man7.org/linux/man-pages/man1/grep.1.html](https://man7.org/linux/man-pages/man1/grep.1.html)
- Sed Manual: [www.gnu.org/software/sed/manual](https://www.gnu.org/software/sed/manual/)
