
# 🗄️ MySQL / MariaDB Database Server

> **Tags:** #linux #mysql #mariadb #banco-de-dados #servicos #sql

---

## 📌 Visão Geral

**MySQL** e **MariaDB** são sistemas de gerenciamento de banco de dados relacionais (RDBMS) de código aberto, amplamente utilizados em aplicações web.

🎯 **Objetivo:** Armazenar, gerenciar e recuperar dados para aplicações.

---

## 📥 Instalação

### MySQL Server

bash
#### Debian/Ubuntu

sudo apt update sudo apt install mysql-server -y
#### Red Hat/CentOS

sudo yum install mysql-server -y
#### Ou

sudo dnf install mysql-server -y

### MariaDB Server (Alternativa ao MySQL)

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-y9wps4ca4" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Debian/Ubuntu</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">apt</span><span> update
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">apt</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">install</span><span> mariadb-server </span><span class="token parameter" style="color:rgb(214, 222, 235)">-y</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Red Hat/CentOS</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> yum </span><span class="token" style="color:rgb(130, 170, 255)">install</span><span> mariadb-server </span><span class="token parameter" style="color:rgb(214, 222, 235)">-y</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ou</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> dnf </span><span class="token" style="color:rgb(130, 170, 255)">install</span><span> mariadb-server </span><span class="token parameter" style="color:rgb(214, 222, 235)">-y</span><span>
</span></code></pre></div>

**Verificar status:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-effw6imkj" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> systemctl status mysql  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ou mariadb</span><span>
</span></code></pre></div>

---

## 🔒 Configuração de Segurança Pós-Instalação

**Descrição:** Executar script de segurança para proteger a instalação.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-xjyl7gmti" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> mysql_secure_installation
</span></code></pre></div>

**Passos do script:**
1. **Validar plugin de senha:** Ativar plugin para senhas fortes.
2. **Definir senha root:** Essencial.
3. **Remover usuários anônimos:** `Y`
4. **Desabilitar login root remoto:** `Y` (para segurança, acesse via SSH e depois MySQL localmente).
5. **Remover banco de dados de teste:** `Y`
6. **Recarregar tabelas de privilégios:** `Y`

---

## 💻 Acesso ao MySQL Shell

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-pn6phvcdx" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Acessar como root (localmente)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> mysql </span><span class="token parameter" style="color:rgb(214, 222, 235)">-u</span><span> root </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Digite a senha root que você definiu</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Acessar como outro usuário</span><span>
</span><span>mysql </span><span class="token parameter" style="color:rgb(214, 222, 235)">-u</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">&lt;</span><span>username</span><span class="token" style="color:rgb(127, 219, 202)">&gt;</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span>
</span></code></pre></div>

---

## 🗄️ Comandos SQL Básicos

### Gerenciamento de Bancos de Dados

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">sql</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-vcxrpg3zg" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-sql" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic">-- Listar bancos de dados</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">SHOW</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">DATABASES</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic">-- Criar um novo banco de dados</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">CREATE</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">DATABASE</span><span> meu_banco</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic">-- Selecionar um banco de dados para uso</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">USE</span><span> meu_banco</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic">-- Deletar um banco de dados</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">DROP</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">DATABASE</span><span> meu_banco</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span></code></pre></div>

---

### Gerenciamento de Tabelas

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">sql</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-1ohiowzsb" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-sql" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic">-- Listar tabelas no banco de dados atual</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">SHOW</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">TABLES</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic">-- Criar uma tabela</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">CREATE</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">TABLE</span><span> usuarios </span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>
</span><span>    id </span><span class="token" style="color:rgb(127, 219, 202)">INT</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">AUTO_INCREMENT</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">PRIMARY</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">KEY</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>
</span><span>    nome </span><span class="token" style="color:rgb(127, 219, 202)">VARCHAR</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(247, 140, 108)">100</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">NOT</span><span> </span><span class="token" style="color:rgb(255, 88, 116)">NULL</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>
</span><span>    email </span><span class="token" style="color:rgb(127, 219, 202)">VARCHAR</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(247, 140, 108)">100</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">UNIQUE</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>
</span><span>    data_cadastro </span><span class="token" style="color:rgb(127, 219, 202)">DATETIME</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">DEFAULT</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">CURRENT_TIMESTAMP</span><span>
</span><span></span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic">-- Descrever a estrutura de uma tabela</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">DESCRIBE</span><span> usuarios</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic">-- Deletar uma tabela</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">DROP</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">TABLE</span><span> usuarios</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span></code></pre></div>

---

### Manipulação de Dados (CRUD)

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">sql</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-qbuldwpfd" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-sql" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic">-- Inserir dados</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">INSERT</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">INTO</span><span> usuarios </span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>nome</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> email</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">VALUES</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(173, 219, 103)">&#x27;Alex Tuma&#x27;</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;alex@exemplo.com&#x27;</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic">-- Selecionar dados</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">SELECT</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">*</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">FROM</span><span> usuarios</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">SELECT</span><span> nome</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> email </span><span class="token" style="color:rgb(127, 219, 202)">FROM</span><span> usuarios </span><span class="token" style="color:rgb(127, 219, 202)">WHERE</span><span> id </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">1</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">SELECT</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">*</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">FROM</span><span> usuarios </span><span class="token" style="color:rgb(127, 219, 202)">WHERE</span><span> nome </span><span class="token" style="color:rgb(127, 219, 202)">LIKE</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;Alex%&#x27;</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic">-- Atualizar dados</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">UPDATE</span><span> usuarios </span><span class="token" style="color:rgb(127, 219, 202)">SET</span><span> email </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;novo_email@exemplo.com&#x27;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">WHERE</span><span> id </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">1</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic">-- Deletar dados</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">DELETE</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">FROM</span><span> usuarios </span><span class="token" style="color:rgb(127, 219, 202)">WHERE</span><span> id </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">1</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span></code></pre></div>

---

## 👤 Gerenciamento de Usuários e Permissões

### Criar Usuário

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">sql</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-u8ar9z5tx" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-sql" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic">-- Criar usuário local (acesso apenas de localhost)</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">CREATE</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">USER</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;meu_usuario&#x27;</span><span class="token" style="color:rgb(214, 222, 235)">@&#x27;localhost&#x27;</span><span> IDENTIFIED </span><span class="token" style="color:rgb(127, 219, 202)">BY</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;minha_senha_forte&#x27;</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic">-- Criar usuário com acesso de qualquer host (menos seguro)</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">CREATE</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">USER</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;meu_usuario&#x27;</span><span class="token" style="color:rgb(214, 222, 235)">@&#x27;%&#x27;</span><span> IDENTIFIED </span><span class="token" style="color:rgb(127, 219, 202)">BY</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;minha_senha_forte&#x27;</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic">-- MySQL 8.0+ (alterar método de autenticação se necessário para compatibilidade)</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">ALTER</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">USER</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;meu_usuario&#x27;</span><span class="token" style="color:rgb(214, 222, 235)">@&#x27;%&#x27;</span><span> IDENTIFIED </span><span class="token" style="color:rgb(127, 219, 202)">WITH</span><span> mysql_native_password </span><span class="token" style="color:rgb(127, 219, 202)">BY</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;minha_senha_forte&#x27;</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span></code></pre></div>

---

### Conceder Permissões (GRANT)

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">sql</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-tn5hu47iw" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-sql" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic">-- Conceder todos os privilégios em um banco de dados específico</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">GRANT</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">ALL</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">PRIVILEGES</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">ON</span><span> meu_banco</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span class="token" style="color:rgb(127, 219, 202)">*</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">TO</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;meu_usuario&#x27;</span><span class="token" style="color:rgb(214, 222, 235)">@&#x27;localhost&#x27;</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic">-- Conceder apenas SELECT e INSERT em uma tabela específica</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">GRANT</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">SELECT</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">INSERT</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">ON</span><span> meu_banco</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>usuarios </span><span class="token" style="color:rgb(127, 219, 202)">TO</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;meu_usuario&#x27;</span><span class="token" style="color:rgb(214, 222, 235)">@&#x27;localhost&#x27;</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic">-- Conceder todos os privilégios em todos os bancos (CUIDADO!)</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">GRANT</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">ALL</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">PRIVILEGES</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">ON</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">*</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span class="token" style="color:rgb(127, 219, 202)">*</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">TO</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;meu_usuario&#x27;</span><span class="token" style="color:rgb(214, 222, 235)">@&#x27;localhost&#x27;</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic">-- Aplicar as mudanças de privilégios</span><span>
</span><span>FLUSH </span><span class="token" style="color:rgb(127, 219, 202)">PRIVILEGES</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span></code></pre></div>

---

### Revogar Permissões (REVOKE)

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">sql</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-0in3nkys3" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-sql" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic">-- Revogar privilégios</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">REVOKE</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">ALL</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">PRIVILEGES</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">ON</span><span> meu_banco</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span class="token" style="color:rgb(127, 219, 202)">*</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">FROM</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;meu_usuario&#x27;</span><span class="token" style="color:rgb(214, 222, 235)">@&#x27;localhost&#x27;</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span><span>FLUSH </span><span class="token" style="color:rgb(127, 219, 202)">PRIVILEGES</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span></code></pre></div>

---

### Deletar Usuário

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">sql</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-jfq2h7grf" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-sql" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(127, 219, 202)">DROP</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">USER</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;meu_usuario&#x27;</span><span class="token" style="color:rgb(214, 222, 235)">@&#x27;localhost&#x27;</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span><span>FLUSH </span><span class="token" style="color:rgb(127, 219, 202)">PRIVILEGES</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span></code></pre></div>

---

## ⚙️ Configuração do MySQL

**Arquivo principal:** `/etc/mysql/mysql.conf.d/mysqld.cnf` (Debian/Ubuntu)

**Parâmetros comuns:**
- `bind-address`: Endereço IP para escutar conexões (padrão: `127.0.0.1`). Mude para `0.0.0.0` para acesso externo (com firewall).
- `port`: Porta de escuta (padrão: `3306`).
- `datadir`: Diretório onde os dados são armazenados.
- `log_error`: Arquivo de log de erros.
- `general_log`: Habilitar log geral (CUIDADO: performance).

**Após modificar, reinicie o serviço:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-fipf9a4mk" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> systemctl restart mysql
</span></code></pre></div>

---

## 💾 Backup e Restauração

### Backup de Banco de Dados

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-9qisakpmh" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Backup de um banco de dados</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> mysqldump </span><span class="token parameter" style="color:rgb(214, 222, 235)">-u</span><span> root </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> meu_banco </span><span class="token" style="color:rgb(127, 219, 202)">&gt;</span><span> meu_banco_backup.sql
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Backup de todos os bancos de dados</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> mysqldump </span><span class="token parameter" style="color:rgb(214, 222, 235)">-u</span><span> root </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> --all-databases </span><span class="token" style="color:rgb(127, 219, 202)">&gt;</span><span> all_databases_backup.sql
</span></code></pre></div>

---

### Restauração de Banco de Dados

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-lfjhiup7y" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Criar o banco de dados primeiro (se não existir)</span><span>
</span><span>mysql </span><span class="token parameter" style="color:rgb(214, 222, 235)">-u</span><span> root </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-e</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;CREATE DATABASE meu_banco;&quot;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Restaurar o backup</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> mysql </span><span class="token parameter" style="color:rgb(214, 222, 235)">-u</span><span> root </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> meu_banco </span><span class="token" style="color:rgb(127, 219, 202)">&lt;</span><span> meu_banco_backup.sql
</span></code></pre></div>

---

## 🌐 Acesso Remoto (com Firewall)

1. **Configurar `bind-address`:** Mudar para `0.0.0.0` em `/etc/mysql/mysql.conf.d/mysqld.cnf`.
2. **Reiniciar MySQL:** `sudo systemctl restart mysql`.
3. **Abrir porta no firewall:** `sudo iptables -A INPUT -p tcp --dport 3306 -j ACCEPT`.
4. **Conceder permissões:** `GRANT ALL PRIVILEGES ON meu_banco.* TO 'meu_usuario'@'%' IDENTIFIED BY 'minha_senha_forte';`.

---

## 🛠️ Ferramentas Gráficas

- **phpMyAdmin:** Interface web para gerenciar MySQL.
- **HeidiSQL:** Cliente GUI para Windows.
- **DBeaver:** Cliente GUI universal.

---

## ⚠️ SQL Injection

**Descrição:** Ataque que explora vulnerabilidades em aplicações web para injetar comandos SQL maliciosos.

**Exemplo de bypass de autenticação:**
`' OR 1=1 --`

**Contramedidas:**
- **Prepared Statements** (consultas parametrizadas).
- **Input Validation** (validação de entrada).
- **Least Privilege** (menor privilégio para usuários de banco).
- **Web Application Firewall (WAF)**.

---

## 🔗 Links Relacionados

- [[29_PostgreSQL]]
- [[27_Apache]]
- [[32_Docker]]
- [[OWASP-Top-10]]
- [[19_Hardening-Linux]]

---

## 📚 Referências

- MySQL Official: [www.mysql.com](https://www.mysql.com/)
- MariaDB Official: [mariadb.org](https://mariadb.org/)
- MySQL Documentation: [dev.mysql.com/doc](https://dev.mysql.com/doc/)
- SQL Injection Cheatsheet: [portswigger.net/web-security/sql-injection/cheat-sheet](https://portswigger.net/web-security/sql-injection/cheat-sheet)
