
# 📁 FTP - vsftpd Server

> **Tags:** #linux #ftp #vsftpd #servicos #transferencia-de-arquivos #seguranca

---

## 📌 Visão Geral

**FTP (File Transfer Protocol)** é um protocolo padrão para transferência de arquivos entre um cliente e um servidor. **vsftpd (very secure FTP daemon)** é um servidor FTP popular, conhecido por sua segurança e desempenho.

🎯 **Objetivo:** Configurar um servidor FTP seguro para permitir a transferência de arquivos.

---

## 📥 Instalação

bash
#### Debian/Ubuntu

sudo apt update sudo apt install vsftpd -y
#### Red Hat/CentOS

sudo yum install vsftpd -y
#### Ou

sudo dnf install vsftpd -y
#### Habilitar e iniciar serviço

sudo systemctl enable vsftpd sudo systemctl start vsftpd
#### Verificar status

sudo systemctl status vsftpd


---

## ⚙️ Configuração (vsftpd.conf)

**Arquivo principal:** `/etc/vsftpd.conf`

**⚠️ Sempre faça backup antes de editar:** `sudo cp /etc/vsftpd.conf /etc/vsftpd.conf.bak`

### Parâmetros de Segurança e Funcionalidade

| Parâmetro | Valor Recomendado | Descrição |
|-----------|-------------------|-----------|
| `anonymous_enable` | `NO` | Desabilitar login anônimo (segurança) |
| `local_enable` | `YES` | Permitir login de usuários locais do sistema |
| `write_enable` | `YES` | Permitir operações de escrita (upload, delete) |
| `chroot_local_user` | `YES` | Enjaular usuários em seus diretórios home (segurança) |
| `allow_writeable_chroot` | `YES` | Permitir diretórios chroot graváveis (necessário para alguns clientes) |
| `dirmessage_enable` | `YES` | Exibir mensagem de diretório (`.message`) |
| `xferlog_enable` | `YES` | Habilitar log de transferências |
| `xferlog_file` | `/var/log/vsftpd.log` | Caminho do log de transferências |
| `connect_from_port_20` | `YES` | Usar porta 20 para conexões de dados (modo ativo) |
| `pasv_enable` | `YES` | Habilitar modo passivo |
| `pasv_min_port` | `40000` | Porta mínima para modo passivo |
| `pasv_max_port` | `50000` | Porta máxima para modo passivo |
| `listen` | `YES` | vsftpd roda em modo standalone (IPv4) |
| `listen_ipv6` | `NO` | vsftpd roda em modo standalone (IPv6) |
| `ssl_enable` | `YES` | Habilitar SSL/TLS (FTPS) |
| `rsa_cert_file` | `/etc/ssl/certs/ssl-cert-snakeoil.pem` | Caminho do certificado SSL |
| `rsa_private_key_file` | `/etc/ssl/private/ssl-cert-snakeoil.key` | Caminho da chave privada SSL |

---

### Exemplo de Configuração Segura

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">ini</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-gxaioup26" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-ini" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># /etc/vsftpd.conf</span><span>
</span><span></span><span class="token key" style="color:rgb(173, 219, 103);font-style:italic">listen</span><span class="token" style="color:rgb(199, 146, 234)">=</span><span class="token value" style="color:rgb(255, 203, 139)">YES</span><span>
</span><span></span><span class="token key" style="color:rgb(173, 219, 103);font-style:italic">listen_ipv6</span><span class="token" style="color:rgb(199, 146, 234)">=</span><span class="token value" style="color:rgb(255, 203, 139)">NO</span><span>
</span>
<span></span><span class="token key" style="color:rgb(173, 219, 103);font-style:italic">anonymous_enable</span><span class="token" style="color:rgb(199, 146, 234)">=</span><span class="token value" style="color:rgb(255, 203, 139)">NO</span><span>
</span><span></span><span class="token key" style="color:rgb(173, 219, 103);font-style:italic">local_enable</span><span class="token" style="color:rgb(199, 146, 234)">=</span><span class="token value" style="color:rgb(255, 203, 139)">YES</span><span>
</span><span></span><span class="token key" style="color:rgb(173, 219, 103);font-style:italic">write_enable</span><span class="token" style="color:rgb(199, 146, 234)">=</span><span class="token value" style="color:rgb(255, 203, 139)">YES</span><span>
</span>
<span></span><span class="token key" style="color:rgb(173, 219, 103);font-style:italic">dirmessage_enable</span><span class="token" style="color:rgb(199, 146, 234)">=</span><span class="token value" style="color:rgb(255, 203, 139)">YES</span><span>
</span><span></span><span class="token key" style="color:rgb(173, 219, 103);font-style:italic">use_localtime</span><span class="token" style="color:rgb(199, 146, 234)">=</span><span class="token value" style="color:rgb(255, 203, 139)">YES</span><span>
</span><span></span><span class="token key" style="color:rgb(173, 219, 103);font-style:italic">xferlog_enable</span><span class="token" style="color:rgb(199, 146, 234)">=</span><span class="token value" style="color:rgb(255, 203, 139)">YES</span><span>
</span><span></span><span class="token key" style="color:rgb(173, 219, 103);font-style:italic">connect_from_port_20</span><span class="token" style="color:rgb(199, 146, 234)">=</span><span class="token value" style="color:rgb(255, 203, 139)">YES</span><span>
</span><span></span><span class="token key" style="color:rgb(173, 219, 103);font-style:italic">xferlog_file</span><span class="token" style="color:rgb(199, 146, 234)">=</span><span class="token value" style="color:rgb(255, 203, 139)">/var/log/vsftpd.log</span><span>
</span><span></span><span class="token key" style="color:rgb(173, 219, 103);font-style:italic">xferlog_std_format</span><span class="token" style="color:rgb(199, 146, 234)">=</span><span class="token value" style="color:rgb(255, 203, 139)">YES</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Chroot para segurança</span><span>
</span><span></span><span class="token key" style="color:rgb(173, 219, 103);font-style:italic">chroot_local_user</span><span class="token" style="color:rgb(199, 146, 234)">=</span><span class="token value" style="color:rgb(255, 203, 139)">YES</span><span>
</span><span></span><span class="token key" style="color:rgb(173, 219, 103);font-style:italic">allow_writeable_chroot</span><span class="token" style="color:rgb(199, 146, 234)">=</span><span class="token value" style="color:rgb(255, 203, 139)">YES # Necessário se o diretório home for gravável</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Modo passivo (necessário para muitos clientes e NAT)</span><span>
</span><span></span><span class="token key" style="color:rgb(173, 219, 103);font-style:italic">pasv_enable</span><span class="token" style="color:rgb(199, 146, 234)">=</span><span class="token value" style="color:rgb(255, 203, 139)">YES</span><span>
</span><span></span><span class="token key" style="color:rgb(173, 219, 103);font-style:italic">pasv_min_port</span><span class="token" style="color:rgb(199, 146, 234)">=</span><span class="token value" style="color:rgb(255, 203, 139)">40000</span><span>
</span><span></span><span class="token key" style="color:rgb(173, 219, 103);font-style:italic">pasv_max_port</span><span class="token" style="color:rgb(199, 146, 234)">=</span><span class="token value" style="color:rgb(255, 203, 139)">50000</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Limitar usuários a seus diretórios home</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># user_sub_token=$USER</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># local_root=/home/$USER/ftp_root # Se quiser um subdiretório específico</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Habilitar SSL/TLS (FTPS)</span><span>
</span><span></span><span class="token key" style="color:rgb(173, 219, 103);font-style:italic">ssl_enable</span><span class="token" style="color:rgb(199, 146, 234)">=</span><span class="token value" style="color:rgb(255, 203, 139)">YES</span><span>
</span><span></span><span class="token key" style="color:rgb(173, 219, 103);font-style:italic">allow_anon_ssl</span><span class="token" style="color:rgb(199, 146, 234)">=</span><span class="token value" style="color:rgb(255, 203, 139)">NO</span><span>
</span><span></span><span class="token key" style="color:rgb(173, 219, 103);font-style:italic">force_local_data_ssl</span><span class="token" style="color:rgb(199, 146, 234)">=</span><span class="token value" style="color:rgb(255, 203, 139)">YES</span><span>
</span><span></span><span class="token key" style="color:rgb(173, 219, 103);font-style:italic">force_local_logins_ssl</span><span class="token" style="color:rgb(199, 146, 234)">=</span><span class="token value" style="color:rgb(255, 203, 139)">YES</span><span>
</span><span></span><span class="token key" style="color:rgb(173, 219, 103);font-style:italic">ssl_tlsv1_2</span><span class="token" style="color:rgb(199, 146, 234)">=</span><span class="token value" style="color:rgb(255, 203, 139)">YES # Apenas TLSv1.2</span><span>
</span><span></span><span class="token key" style="color:rgb(173, 219, 103);font-style:italic">ssl_sslv2</span><span class="token" style="color:rgb(199, 146, 234)">=</span><span class="token value" style="color:rgb(255, 203, 139)">NO</span><span>
</span><span></span><span class="token key" style="color:rgb(173, 219, 103);font-style:italic">ssl_sslv3</span><span class="token" style="color:rgb(199, 146, 234)">=</span><span class="token value" style="color:rgb(255, 203, 139)">NO</span><span>
</span><span></span><span class="token key" style="color:rgb(173, 219, 103);font-style:italic">rsa_cert_file</span><span class="token" style="color:rgb(199, 146, 234)">=</span><span class="token value" style="color:rgb(255, 203, 139)">/etc/ssl/certs/ssl-cert-snakeoil.pem</span><span>
</span><span></span><span class="token key" style="color:rgb(173, 219, 103);font-style:italic">rsa_private_key_file</span><span class="token" style="color:rgb(199, 146, 234)">=</span><span class="token value" style="color:rgb(255, 203, 139)">/etc/ssl/private/ssl-cert-snakeoil.key</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Restringir usuários</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># userlist_enable=YES</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># userlist_deny=NO # Se NO, apenas usuários em userlist_file podem logar</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># userlist_file=/etc/vsftpd.userlist</span><span>
</span></code></pre></div>

**Após modificar, reinicie o serviço:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-n16rtbedd" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> systemctl restart vsftpd
</span></code></pre></div>

---

## 👤 Gerenciamento de Usuários

**Descrição:** Usuários que farão login no FTP devem ser usuários do sistema Linux.

### Criar Usuário FTP

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-dmh4ostn2" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Criar usuário (sem shell de login para segurança)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">useradd</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-m</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-s</span><span> /usr/sbin/nologin ftpuser
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Definir senha</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">passwd</span><span> ftpuser
</span></code></pre></div>

---

### Restringir Usuários (userlist)

**Descrição:** Controlar quais usuários podem ou não acessar o FTP.

1. **Habilitar userlist:**
   `userlist_enable=YES`
2. **Definir comportamento:**
   - `userlist_deny=YES` (padrão): Usuários na lista **NÃO PODEM** logar.
   - `userlist_deny=NO`: Usuários na lista **SÓ PODEM** logar.
3. **Criar arquivo de lista:** `/etc/vsftpd.userlist`

**Exemplo (`/etc/vsftpd.userlist`):**
```

ftpuser outro_usuario

```
---

## 🌐 Acesso com Firewall

**Descrição:** Abrir as portas necessárias no firewall.

- **Porta de controle FTP:** `21/tcp`
- **Porta de dados FTP (modo ativo):** `20/tcp`
- **Portas de dados FTP (modo passivo):** Range definido por `pasv_min_port` e `pasv_max_port` (ex: `40000-50000/tcp`).

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-53ftirg7z" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Abrir porta de controle</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-A</span><span> INPUT </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> tcp </span><span class="token parameter" style="color:rgb(214, 222, 235)">--dport</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">21</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-j</span><span> ACCEPT
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Abrir porta de dados (ativo)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-A</span><span> INPUT </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> tcp </span><span class="token parameter" style="color:rgb(214, 222, 235)">--dport</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">20</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-j</span><span> ACCEPT
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Abrir range de portas para modo passivo</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-A</span><span> INPUT </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> tcp </span><span class="token parameter" style="color:rgb(214, 222, 235)">--dport</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">40000</span><span>:50000 </span><span class="token parameter" style="color:rgb(214, 222, 235)">-j</span><span> ACCEPT
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Permitir conexões estabelecidas</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-A</span><span> INPUT </span><span class="token parameter" style="color:rgb(214, 222, 235)">-m</span><span> state </span><span class="token parameter" style="color:rgb(214, 222, 235)">--state</span><span> ESTABLISHED,RELATED </span><span class="token parameter" style="color:rgb(214, 222, 235)">-j</span><span> ACCEPT
</span></code></pre></div>

---

## 📊 Logs

**Arquivo de log:** `/var/log/vsftpd.log`

**Visualizar logs em tempo real:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-075ntjlzz" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">tail</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-f</span><span> /var/log/vsftpd.log
</span></code></pre></div>

---

## 🔗 Links Relacionados

- [[31_Samba]]
- [[16_SSH]]
- [[19_Hardening-Linux]]
- [[17_Firewall-iptables]]
- [[07_Gerenciamento-de-Usuarios]]

---

## 📚 Referências

- vsftpd Official: [security.appspot.com/vsftpd.html](https://security.appspot.com/vsftpd.html)
- vsftpd Man Page: [man7.org/linux/man-pages/man5/vsftpd.conf.5.html](https://man7.org/linux/man-pages/man5/vsftpd.conf.5.html)
- FTP Hardening: [www.digitalocean.com/community/tutorials/how-to-set-up-vsftpd-for-a-user-s-home-directory-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-vsftpd-for-a-user-s-home-directory-on-ubuntu-16-04)
