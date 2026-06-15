
# 🐘 PostgreSQL Database Server

> **Tags:** #linux #postgresql #banco-de-dados #servicos #sql #open-source

---

## 📌 Visão Geral

**PostgreSQL** é um sistema de gerenciamento de banco de dados relacional (RDBMS) de código aberto, conhecido por sua robustez, confiabilidade e conformidade com padrões SQL.

🎯 **Objetivo:** Fornecer um banco de dados poderoso e extensível para aplicações de missão crítica.

---

## 📥 Instalação

bash
#### Debian/Ubuntu

sudo apt update sudo apt install postgresql postgresql-contrib -y
#### Red Hat/CentOS

sudo yum install postgresql-server postgresql-contrib -y
#### Ou

sudo dnf install postgresql-server postgresql-contrib -y
#### Inicializar banco de dados (apenas Red Hat/CentOS)

#### sudo postgresql-setup initdb

#### Habilitar e iniciar serviço

sudo systemctl enable postgresql sudo systemctl start postgresql

#### Verificar status

sudo systemctl status postgresql

---

## 💻 Acesso ao PostgreSQL Shell (psql)

### Usuário `postgres`

**Descrição:** O PostgreSQL cria um usuário de sistema `postgres` que é o superusuário do banco de dados.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-dthg15nw1" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Trocar para o usuário postgres</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-i</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-u</span><span> postgres
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Acessar o shell psql</span><span>
</span>psql
</code></pre></div>

**Comandos no `psql`:**
- `\l`: Listar bancos de dados.
- `\c <database_name>`: Conectar a um banco de dados.
- `\dt`: Listar tabelas no banco de dados atual.
- `\du`: Listar usuários (roles).
- `\q`: Sair do psql.

---

## 🗄️ Comandos SQL Básicos

### Gerenciamento de Bancos de Dados

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">sql</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-4skgclxcb" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-sql" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic">-- Listar bancos de dados</span><span>
</span>\l
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic">-- Criar um novo banco de dados</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">CREATE</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">DATABASE</span><span> meu_banco</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic">-- Conectar a um banco de dados</span><span>
</span><span>\c meu_banco</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic">-- Deletar um banco de dados</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">DROP</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">DATABASE</span><span> meu_banco</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span></code></pre></div>

---

### Gerenciamento de Tabelas

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">sql</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-g22hf3fdb" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-sql" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic">-- Listar tabelas no banco de dados atual</span><span>
</span>\dt
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic">-- Criar uma tabela</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">CREATE</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">TABLE</span><span> produtos </span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>
</span><span>    id </span><span class="token" style="color:rgb(127, 219, 202)">SERIAL</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">PRIMARY</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">KEY</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>
</span><span>    nome </span><span class="token" style="color:rgb(127, 219, 202)">VARCHAR</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(247, 140, 108)">100</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">NOT</span><span> </span><span class="token" style="color:rgb(255, 88, 116)">NULL</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>
</span><span>    preco </span><span class="token" style="color:rgb(127, 219, 202)">NUMERIC</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(247, 140, 108)">10</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">2</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">NOT</span><span> </span><span class="token" style="color:rgb(255, 88, 116)">NULL</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>
</span><span>    estoque </span><span class="token" style="color:rgb(127, 219, 202)">INT</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">DEFAULT</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">0</span><span>
</span><span></span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic">-- Descrever a estrutura de uma tabela</span><span>
</span><span>\d produtos</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic">-- Deletar uma tabela</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">DROP</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">TABLE</span><span> produtos</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span></code></pre></div>

---

### Manipulação de Dados (CRUD)

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">sql</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-0i1qg36r6" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-sql" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic">-- Inserir dados</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">INSERT</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">INTO</span><span> produtos </span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>nome</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> preco</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> estoque</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">VALUES</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(173, 219, 103)">&#x27;Laptop&#x27;</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">1200.00</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">50</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic">-- Selecionar dados</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">SELECT</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">*</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">FROM</span><span> produtos</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">SELECT</span><span> nome</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> preco </span><span class="token" style="color:rgb(127, 219, 202)">FROM</span><span> produtos </span><span class="token" style="color:rgb(127, 219, 202)">WHERE</span><span> id </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">1</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic">-- Atualizar dados</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">UPDATE</span><span> produtos </span><span class="token" style="color:rgb(127, 219, 202)">SET</span><span> preco </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">1150.00</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">WHERE</span><span> id </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">1</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic">-- Deletar dados</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">DELETE</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">FROM</span><span> produtos </span><span class="token" style="color:rgb(127, 219, 202)">WHERE</span><span> id </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">1</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span></code></pre></div>

---

## 👤 Gerenciamento de Usuários (Roles) e Permissões

**Descrição:** No PostgreSQL, usuários são chamados de "roles".

### Criar Usuário (Role)

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">sql</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-2xmf2jywd" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-sql" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic">-- Criar um usuário com senha</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">CREATE</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">USER</span><span> meu_usuario </span><span class="token" style="color:rgb(127, 219, 202)">WITH</span><span> PASSWORD </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;minha_senha_forte&#x27;</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic">-- Criar um usuário com privilégios de superusuário (CUIDADO!)</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">CREATE</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">USER</span><span> admin_usuario </span><span class="token" style="color:rgb(127, 219, 202)">WITH</span><span> SUPERUSER PASSWORD </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;senha_admin&#x27;</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic">-- Criar um usuário que pode criar bancos de dados</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">CREATE</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">USER</span><span> db_creator </span><span class="token" style="color:rgb(127, 219, 202)">WITH</span><span> CREATEDB PASSWORD </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;senha_db&#x27;</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span></code></pre></div>

---

### Conceder Permissões (GRANT)

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">sql</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-csi0l55t8" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-sql" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic">-- Conceder todos os privilégios em um banco de dados</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">GRANT</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">ALL</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">PRIVILEGES</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">ON</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">DATABASE</span><span> meu_banco </span><span class="token" style="color:rgb(127, 219, 202)">TO</span><span> meu_usuario</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic">-- Conceder privilégios em uma tabela</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">GRANT</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">SELECT</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">INSERT</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">ON</span><span> produtos </span><span class="token" style="color:rgb(127, 219, 202)">TO</span><span> meu_usuario</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic">-- Conceder privilégios para todas as tabelas futuras em um schema</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">ALTER</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">DEFAULT</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">PRIVILEGES</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">IN</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">SCHEMA</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">public</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">GRANT</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">SELECT</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">INSERT</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">ON</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">TABLES</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">TO</span><span> meu_usuario</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span></code></pre></div>

---

### Revogar Permissões (REVOKE)

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">sql</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-u218d0s4s" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-sql" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic">-- Revogar privilégios</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">REVOKE</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">ALL</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">PRIVILEGES</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">ON</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">DATABASE</span><span> meu_banco </span><span class="token" style="color:rgb(127, 219, 202)">FROM</span><span> meu_usuario</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span></code></pre></div>

---

### Deletar Usuário (Role)

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">sql</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-p7o57qii4" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-sql" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(127, 219, 202)">DROP</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">USER</span><span> meu_usuario</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span></code></pre></div>

---

## ⚙️ Configuração do PostgreSQL

**Arquivo principal:** `/etc/postgresql/<version>/main/postgresql.conf`

**Parâmetros comuns:**
- `listen_addresses`: Endereços IP para escutar conexões (padrão: `localhost`). Mude para `'*'` para acesso externo (com firewall).
- `port`: Porta de escuta (padrão: `5432`).
- `data_directory`: Diretório onde os dados são armazenados.
- `log_destination`: Onde os logs são enviados.

**Arquivo de autenticação:** `/etc/postgresql/<version>/main/pg_hba.conf`

**Exemplo de `pg_hba.conf` para acesso remoto:**
```

# TYPE DATABASE USER ADDRESS METHOD

host all all 192.168.1.0/24 md5 # Permite acesso da rede 192.168.1.0/24 com senha MD5 host all all 0.0.0.0/0 md5 # Permite acesso de qualquer IP (CUIDADO!)

```
**Após modificar, reinicie o serviço:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-g2v1csk0v" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> systemctl restart postgresql
</span></code></pre></div>

---

## 🌐 Acesso Remoto (com Firewall)

1. **Configurar `listen_addresses`:** Mudar para `'*'` em `postgresql.conf`.
2. **Configurar `pg_hba.conf`:** Adicionar linha para permitir acesso da rede desejada.
3. **Reiniciar PostgreSQL:** `sudo systemctl restart postgresql`.
4. **Abrir porta no firewall:** `sudo iptables -A INPUT -p tcp --dport 5432 -j ACCEPT`.

---

## 💾 Backup e Restauração

### Backup de Banco de Dados

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-eucbzu2jy" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Backup de um banco de dados</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-u</span><span> postgres pg_dump meu_banco </span><span class="token" style="color:rgb(127, 219, 202)">&gt;</span><span> meu_banco_backup.sql
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Backup de todos os bancos de dados</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-u</span><span> postgres pg_dumpall </span><span class="token" style="color:rgb(127, 219, 202)">&gt;</span><span> all_databases_backup.sql
</span></code></pre></div>

---

### Restauração de Banco de Dados

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-69c9tw9tg" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Criar o banco de dados primeiro (se não existir)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-u</span><span> postgres psql </span><span class="token parameter" style="color:rgb(214, 222, 235)">-c</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;CREATE DATABASE meu_banco;&quot;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Restaurar o backup</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-u</span><span> postgres psql meu_banco </span><span class="token" style="color:rgb(127, 219, 202)">&lt;</span><span> meu_banco_backup.sql
</span></code></pre></div>

---

## 🔗 Links Relacionados

- [[28_MySQL]]
- [[32_Docker]]
- [[19_Hardening-Linux]]
- [[22_Auditoria-e-Logs]]

---

## 📚 Referências

- PostgreSQL Official: [www.postgresql.org](https://www.postgresql.org/)
- PostgreSQL Documentation: [www.postgresql.org/docs](https://www.postgresql.org/docs/)
- Pg_hba.conf: [www.postgresql.org/docs/current/auth-pg-hba-conf.html](https://www.postgresql.org/docs/current/auth-pg-hba-conf.html)
