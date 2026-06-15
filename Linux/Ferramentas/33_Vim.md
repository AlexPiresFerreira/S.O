
# 📝 Vim - Editor de Texto Avançado

> **Tags:** #linux #vim #editor #terminal #produtividade #shell

---

## 📌 Visão Geral

**Vim (Vi IMproved)** é um editor de texto de terminal poderoso, altamente configurável e eficiente, popular entre programadores e administradores de sistema.

🎯 **Objetivo:** Dominar a edição de texto no terminal de forma rápida e eficiente.

---

## 📥 Instalação

bash
#### Debian/Ubuntu

sudo apt install vim
#### Red Hat/CentOS

sudo yum install vim
#### Ou

sudo dnf install vim


---

## 📊 Modos de Operação

O Vim opera em diferentes modos, cada um com uma função específica.

### 1. Modo Normal (Command Mode)

**Descrição:** Modo padrão ao abrir o Vim. Usado para navegação, exclusão, cópia, colagem e execução de comandos.

- **Entrar:** Pressione `Esc`.

---

### 2. Modo Inserção (Insert Mode)

**Descrição:** Usado para digitar texto.

- **Entrar:** Pressione `i`, `a`, `o`, `I`, `A`, `O`.
- **Sair:** Pressione `Esc` para voltar ao Modo Normal.

---

### 3. Modo Visual (Visual Mode)

**Descrição:** Usado para selecionar blocos de texto.

- **Entrar:** Pressione `v` (caractere), `V` (linha), `Ctrl+v` (bloco).
- **Sair:** Pressione `Esc`.

---

### 4. Modo Linha de Comando (Ex Mode)

**Descrição:** Usado para executar comandos do Vim (salvar, sair, buscar, substituir).

- **Entrar:** Pressione `:` (dois pontos) no Modo Normal.
- **Sair:** Pressione `Enter` (executa o comando) ou `Esc` (cancela).

---

## 💻 Comandos Básicos

### Abrir/Criar Arquivo

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-e5md6hjn3" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">vim</span><span> arquivo.txt
</span></code></pre></div>

---

### Sair do Vim

| Comando | Descrição |
|---------|-----------|
| `:q` | Sair (se nenhuma alteração foi feita) |
| `:q!` | Sair sem salvar alterações (forçar) |
| `:w` | Salvar o arquivo |
| `:wq` | Salvar e sair |
| `:x` | Salvar e sair (similar a `:wq`) |
| `ZZ` | Salvar e sair (atalho no Modo Normal) |
| `ZQ` | Sair sem salvar (atalho no Modo Normal) |

---

## 🚶 Navegação (Modo Normal)

| Comando | Descrição |
|---------|-----------|
| `h` | Esquerda (um caractere) |
| `j` | Baixo (uma linha) |
| `k` | Cima (uma linha) |
| `l` | Direita (um caractere) |
| `w` | Próxima palavra |
| `b` | Palavra anterior |
| `e` | Fim da palavra |
| `0` ou `^` | Início da linha |
| `$` | Fim da linha |
| `gg` | Início do arquivo |
| `G` | Fim do arquivo |
| `[num]G` | Ir para a linha `[num]` |
| `Ctrl+f` | Avançar uma tela |
| `Ctrl+b` | Voltar uma tela |

---

## ✏️ Modo Inserção

| Comando | Descrição |
|---------|-----------|
| `i` | Inserir antes do cursor |
| `a` | Inserir após o cursor |
| `o` | Inserir nova linha abaixo |
| `I` | Inserir no início da linha |
| `A` | Inserir no final da linha |
| `O` | Inserir nova linha acima |

---

## ✂️ Edição (Modo Normal)

### Excluir (Delete)

| Comando | Descrição |
|---------|-----------|
| `x` | Excluir caractere sob o cursor |
| `dw` | Excluir palavra |
| `dd` | Excluir linha atual |
| `[num]dd` | Excluir `[num]` linhas |
| `D` | Excluir do cursor até o fim da linha |

---

### Copiar (Yank)

| Comando | Descrição |
|---------|-----------|
| `yw` | Copiar palavra |
| `yy` | Copiar linha atual |
| `[num]yy` | Copiar `[num]` linhas |
| `Y` | Copiar linha (similar a `yy`) |

---

### Colar (Paste)

| Comando | Descrição |
|---------|-----------|
| `p` | Colar após o cursor/linha |
| `P` | Colar antes do cursor/linha |

---

### Mudar (Change)

| Comando | Descrição |
|---------|-----------|
| `cw` | Mudar palavra (exclui e entra em modo inserção) |
| `cc` | Mudar linha (exclui e entra em modo inserção) |
| `C` | Mudar do cursor até o fim da linha |

---

### Desfazer/Refazer

| Comando | Descrição |
|---------|-----------|
| `u` | Desfazer última alteração |
| `Ctrl+r` | Refazer alteração |

---

## 🔎 Busca e Substituição (Modo Linha de Comando)

### Buscar

| Comando | Descrição |
|---------|-----------|
| `:/<palavra>` | Buscar "palavra" para frente |
| `:?<palavra>` | Buscar "palavra" para trás |
| `n` | Próxima ocorrência |
| `N` | Ocorrência anterior |

---

### Substituir

| Comando | Descrição |
|---------|-----------|
| `:%s/antiga/nova/g` | Substituir "antiga" por "nova" em todo o arquivo (global) |
| `:%s/antiga/nova/gc` | Substituir com confirmação |
| `:1,10s/antiga/nova/g` | Substituir nas linhas 1 a 10 |

---

## ⚙️ Configurações Úteis (Modo Linha de Comando)

| Comando | Descrição |
|---------|-----------|
| `:set number` | Mostrar números de linha |
| `:set nonumber` | Esconder números de linha |
| `:set hlsearch` | Destacar resultados da busca |
| `:set nohlsearch` | Desabilitar destaque da busca |
| `:set autoindent` | Indentação automática |
| `:syntax on` | Habilitar destaque de sintaxe |
| `:colorscheme <nome>` | Mudar esquema de cores (ex: `desert`, `molokai`) |

**Configuração permanente:** Adicione estas linhas ao arquivo `~/.vimrc`.

---

## 🔗 Links Relacionados

- [[23_Bash-Scripting]]
- [[04_Gerenciamento-de-Arquivos]]
- [[25_Expressoes-Regulares]]

---

## 📚 Referências

- OpenVim (tutorial interativo): [openvim.com](https://openvim.com/)
- Vim Adventures (jogo para aprender Vim): [vim-adventures.com](https://vim-adventures.com/)
- Vim Cheat Sheet: [vim.rtorr.com](https://vim.rtorr.com/)
- Vim Wiki: [vim.fandom.com/wiki/Vim_Tips_Wiki](https://vim.fandom.com/wiki/Vim_Tips_Wiki)