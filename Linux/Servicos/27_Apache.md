
# 🌐 Apache HTTP Server

> **Tags:** #linux #apache #web-server #servicos #http #https

---

## 📌 Visão Geral

**Apache HTTP Server** (comumente chamado de Apache) é um dos servidores web mais populares e amplamente utilizados no mundo.

🎯 **Objetivo:** Servir conteúdo web (páginas HTML, imagens, vídeos) e aplicações dinâmicas.

---

## 📥 Instalação

bash
#### Debian/Ubuntu

sudo apt update sudo apt install apache2 -y
#### Red Hat/CentOS

sudo yum install httpd -y
#### Ou

sudo dnf install httpd -y
#### Verificar status

sudo systemctl status apache2 # Debian/Ubuntu sudo systemctl status httpd # Red Hat/CentOS
#### Habilitar no boot

sudo systemctl enable apache2 sudo systemctl start apache2

---

## 📊 Arquivos e Diretórios Principais

| Caminho | Descrição |
|---------|-----------|
| `/etc/apache2/` | Diretório de configuração principal (Debian/Ubuntu) |
| `/etc/httpd/` | Diretório de configuração principal (Red Hat/CentOS) |
| `/var/www/html/` | Document root padrão (onde os arquivos web são servidos) |
| `/etc/apache2/sites-available/` | Arquivos de configuração de Virtual Hosts disponíveis |
| `/etc/apache2/sites-enabled/` | Links simbólicos para Virtual Hosts ativos |
| `/var/log/apache2/` | Diretório de logs (access.log, error.log) |

---

## ⚙️ Configuração Básica

### Document Root

**Descrição:** O diretório onde o Apache busca os arquivos para servir.

**Padrão:** `/var/www/html/`

**Exemplo:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">html</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-xbkm7p9jc" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-html" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic">&lt;!-- /var/www/html/index.html --&gt;</span><span>
</span><span></span><span class="token" style="color:rgb(199, 146, 234);font-style:italic">&lt;!</span><span class="token doctype-tag" style="color:rgb(199, 146, 234);font-style:italic">DOCTYPE</span><span class="token" style="color:rgb(199, 146, 234);font-style:italic"> </span><span class="token name" style="color:rgb(199, 146, 234);font-style:italic">html</span><span class="token" style="color:rgb(199, 146, 234);font-style:italic">&gt;</span><span>
</span><span></span><span class="token" style="color:rgb(199, 146, 234)">&lt;</span><span class="token" style="color:rgb(127, 219, 202)">html</span><span class="token" style="color:rgb(199, 146, 234)">&gt;</span><span>
</span><span></span><span class="token" style="color:rgb(199, 146, 234)">&lt;</span><span class="token" style="color:rgb(127, 219, 202)">head</span><span class="token" style="color:rgb(199, 146, 234)">&gt;</span><span>
</span><span>    </span><span class="token" style="color:rgb(199, 146, 234)">&lt;</span><span class="token" style="color:rgb(127, 219, 202)">title</span><span class="token" style="color:rgb(199, 146, 234)">&gt;</span><span>Meu Servidor Apache</span><span class="token" style="color:rgb(199, 146, 234)">&lt;/</span><span class="token" style="color:rgb(127, 219, 202)">title</span><span class="token" style="color:rgb(199, 146, 234)">&gt;</span><span>
</span><span></span><span class="token" style="color:rgb(199, 146, 234)">&lt;/</span><span class="token" style="color:rgb(127, 219, 202)">head</span><span class="token" style="color:rgb(199, 146, 234)">&gt;</span><span>
</span><span></span><span class="token" style="color:rgb(199, 146, 234)">&lt;</span><span class="token" style="color:rgb(127, 219, 202)">body</span><span class="token" style="color:rgb(199, 146, 234)">&gt;</span><span>
</span><span>    </span><span class="token" style="color:rgb(199, 146, 234)">&lt;</span><span class="token" style="color:rgb(127, 219, 202)">h1</span><span class="token" style="color:rgb(199, 146, 234)">&gt;</span><span>Olá do Apache!</span><span class="token" style="color:rgb(199, 146, 234)">&lt;/</span><span class="token" style="color:rgb(127, 219, 202)">h1</span><span class="token" style="color:rgb(199, 146, 234)">&gt;</span><span>
</span><span></span><span class="token" style="color:rgb(199, 146, 234)">&lt;/</span><span class="token" style="color:rgb(127, 219, 202)">body</span><span class="token" style="color:rgb(199, 146, 234)">&gt;</span><span>
</span><span></span><span class="token" style="color:rgb(199, 146, 234)">&lt;/</span><span class="token" style="color:rgb(127, 219, 202)">html</span><span class="token" style="color:rgb(199, 146, 234)">&gt;</span><span>
</span></code></pre></div>

---

### Virtual Hosts

**Descrição:** Permitem hospedar múltiplos sites (domínios) no mesmo servidor Apache.

**Exemplo de Virtual Host (`/etc/apache2/sites-available/meusite.conf`):**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">apache</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-bpphp4q4p" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-apache" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span>&lt;VirtualHost *:80&gt;
</span>    ServerAdmin webmaster@meusite.com
<!-- -->    ServerName meusite.com
<!-- -->    ServerAlias www.meusite.com
<!-- -->    DocumentRoot /var/www/meusite
<!-- -->
<!-- -->    &lt;Directory /var/www/meusite&gt;
<!-- -->        Options Indexes FollowSymLinks
<!-- -->        AllowOverride All
<!-- -->        Require all granted
<!-- -->    &lt;/Directory&gt;
<!-- -->
<!-- -->    ErrorLog ${APACHE_LOG_DIR}/meusite_error.log
<!-- -->    CustomLog ${APACHE_LOG_DIR}/meusite_access.log combined
<!-- -->&lt;/VirtualHost&gt;
</code></pre></div>

**Ativar Virtual Host:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-0kgz9qrfz" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Criar diretório para o site</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">mkdir</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> /var/www/meusite
</span><span></span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;&lt;h1&gt;Bem-vindo ao meu site!&lt;/h1&gt;&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">tee</span><span> /var/www/meusite/index.html
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Habilitar o site</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> a2ensite meusite.conf
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Desabilitar o site padrão (opcional)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> a2dissite 000-default.conf
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Testar configuração</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> apachectl configtest
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Recarregar Apache</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> systemctl reload apache2
</span></code></pre></div>

---

## 🔒 HTTPS com Let's Encrypt

**Descrição:** Instalar certificados SSL/TLS gratuitos para habilitar HTTPS.

### 1. Instalar Certbot

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-7buwd7d9l" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Debian/Ubuntu</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">apt</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">install</span><span> certbot python3-certbot-apache </span><span class="token parameter" style="color:rgb(214, 222, 235)">-y</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Red Hat/CentOS</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> yum </span><span class="token" style="color:rgb(130, 170, 255)">install</span><span> certbot python3-certbot-apache </span><span class="token parameter" style="color:rgb(214, 222, 235)">-y</span><span>
</span></code></pre></div>

### 2. Obter Certificado

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-j0cthhoul" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Para um domínio (ex: meusite.com)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> certbot </span><span class="token parameter" style="color:rgb(214, 222, 235)">--apache</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-d</span><span> meusite.com </span><span class="token parameter" style="color:rgb(214, 222, 235)">-d</span><span> www.meusite.com
</span></code></pre></div>
- Siga as instruções interativas.
- O Certbot irá configurar automaticamente o Virtual Host para HTTPS.

### 3. Renovação Automática

- O Certbot já configura um cron job ou timer do Systemd para renovar os certificados automaticamente.
- Testar renovação: `sudo certbot renew --dry-run`

---

## 🛠️ Módulos Úteis

### Habilitar Módulos

`sudo a2enmod <module_name>` (Debian/Ubuntu)
`sudo systemctl restart apache2`

**Exemplos:**
- `mod_rewrite`: Para URLs amigáveis.
- `mod_ssl`: Para HTTPS.
- `mod_headers`: Para manipular cabeçalhos HTTP.
- `mod_security2`: Para Web Application Firewall (WAF).

---

## 📊 Logs

- **Access Log:** `/var/log/apache2/access.log` (registra todas as requisições).
- **Error Log:** `/var/log/apache2/error.log` (registra erros do servidor).

**Visualizar logs em tempo real:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-nm94978ri" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">tail</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-f</span><span> /var/log/apache2/access.log
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">tail</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-f</span><span> /var/log/apache2/error.log
</span></code></pre></div>

---

## ⚠️ Segurança (Hardening)

- **Manter atualizado:** `sudo apt update && sudo apt upgrade`
- **Desabilitar diretórios de listagem:** `Options -Indexes` no `<Directory>`.
- **Remover páginas padrão:** `index.html`, `info.php`.
- **ModSecurity:** Instalar e configurar um WAF.
- **Server Signature:** Ocultar versão do Apache.

**Exemplo (`/etc/apache2/conf-enabled/security.conf`):**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">apache</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-oeuzrl6yz" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-apache" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span>ServerTokens Prod       # Mostra apenas &quot;Apache&quot;
</span>ServerSignature Off     # Desabilita assinatura no rodapé de páginas de erro
</code></pre></div>

---

## 🔗 Links Relacionados

- [[99__Instalao_e_subir_servios]]
- [[19_Hardening-Linux]]
- [[22_Auditoria-e-Logs]]
- [[HTTP-Status-Codes]]
- [[OWASP-Top-10]]

---

## 📚 Referências

- Apache Official: [httpd.apache.org](https://httpd.apache.org/)
- Ubuntu Apache Docs: [help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
- Certbot: [certbot.eff.org](https://certbot.eff.org/)
