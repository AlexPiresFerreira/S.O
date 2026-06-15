
# 📁 Samba - Compartilhamento de Arquivos SMB/CIFS

> **Tags:** #linux #samba #compartilhamento #smb #cifs #windows #servicos

---

## 📌 Visão Geral

**Samba** é uma implementação de código aberto do protocolo de rede **SMB/CIFS (Server Message Block/Common Internet File System)**, permitindo que sistemas Linux/Unix compartilhem arquivos e impressoras com clientes Windows.

🎯 **Objetivo:** Integrar sistemas Linux em ambientes de rede Windows para compartilhamento de recursos.

---

## 📥 Instalação

bash
#### Debian/Ubuntu

sudo apt update sudo apt install samba -y
#### Red Hat/CentOS

sudo yum install samba -y
#### Ou

sudo dnf install samba -y
#### Habilitar e iniciar serviço

sudo systemctl enable smbd nmbd sudo systemctl start smbd nmbd
#### Verificar status

sudo systemctl status smbd sudo systemctl status nmbd


---

## ⚙️ Configuração (smb.conf)

**Arquivo principal:** `/etc/samba/smb.conf`

**⚠️ Sempre faça backup antes de editar:** `sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.bak`

### Seção `[global]`

**Descrição:** Configurações gerais do servidor Samba.

| Parâmetro | Valor Exemplo | Descrição |
|-----------|---------------|-----------|
| `workgroup` | `WORKGROUP` | Nome do grupo de trabalho (Windows) |
| `netbios name` | `LINUXSERVER` | Nome NetBIOS do servidor |
| `security` | `user` | Modo de segurança (autenticação por usuário) |
| `map to guest` | `Bad User` | Mapeia usuários desconhecidos para convidado |
| `dns proxy` | `no` | Desabilita proxy DNS (geralmente não necessário) |
| `log file` | `/var/log/samba/log.%m` | Arquivo de log por máquina cliente |
| `max log size` | `1000` | Tamanho máximo do log em KB |

---

### Seção de Compartilhamento `[<nome_do_compartilhamento>]`

**Descrição:** Define um recurso a ser compartilhado.

| Parâmetro | Valor Exemplo | Descrição |
|-----------|---------------|-----------|
| `path` | `/srv/samba/compartilhado` | Caminho do diretório a ser compartilhado |
| `browseable` | `yes` | Visível na lista de compartilhamentos |
| `writable` | `yes` | Permitir escrita no compartilhamento |
| `guest ok` | `no` | Não permitir acesso de convidado |
| `read only` | `no` | Não é somente leitura (permite escrita) |
| `valid users` | `usuario1, @grupo_samba` | Usuários ou grupos permitidos |
| `force user` | `usuario_linux` | Força todos os usuários a agir como este usuário Linux |
| `create mask` | `0664` | Permissões padrão para novos arquivos |
| `directory mask` | `0775` | Permissões padrão para novos diretórios |

---

### Exemplo de Configuração de Compartilhamento

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">ini</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-seftul7j7" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-ini" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># /etc/samba/smb.conf (adicionar ao final)</span><span>
</span>
<span></span><span class="token section" style="color:rgb(199, 146, 234)">[</span><span class="token section section-name" style="color:rgb(199, 146, 234);font-style:italic">global</span><span class="token section" style="color:rgb(199, 146, 234)">]</span><span>
</span><span>   </span><span class="token key" style="color:rgb(173, 219, 103);font-style:italic">workgroup</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">=</span><span> </span><span class="token value" style="color:rgb(255, 203, 139)">WORKGROUP</span><span>
</span><span>   </span><span class="token key" style="color:rgb(173, 219, 103);font-style:italic">netbios name</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">=</span><span> </span><span class="token value" style="color:rgb(255, 203, 139)">LINUXSERVER</span><span>
</span><span>   </span><span class="token key" style="color:rgb(173, 219, 103);font-style:italic">security</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">=</span><span> </span><span class="token value" style="color:rgb(255, 203, 139)">user</span><span>
</span><span>   </span><span class="token key" style="color:rgb(173, 219, 103);font-style:italic">map to guest</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">=</span><span> </span><span class="token value" style="color:rgb(255, 203, 139)">Bad User</span><span>
</span><span>   </span><span class="token key" style="color:rgb(173, 219, 103);font-style:italic">dns proxy</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">=</span><span> </span><span class="token value" style="color:rgb(255, 203, 139)">no</span><span>
</span>
<span></span><span class="token section" style="color:rgb(199, 146, 234)">[</span><span class="token section section-name" style="color:rgb(199, 146, 234);font-style:italic">Compartilhado</span><span class="token section" style="color:rgb(199, 146, 234)">]</span><span>
</span><span>   </span><span class="token key" style="color:rgb(173, 219, 103);font-style:italic">comment</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">=</span><span> </span><span class="token value" style="color:rgb(255, 203, 139)">Compartilhamento de Arquivos</span><span>
</span><span>   </span><span class="token key" style="color:rgb(173, 219, 103);font-style:italic">path</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">=</span><span> </span><span class="token value" style="color:rgb(255, 203, 139)">/srv/samba/compartilhado</span><span>
</span><span>   </span><span class="token key" style="color:rgb(173, 219, 103);font-style:italic">browseable</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">=</span><span> </span><span class="token value" style="color:rgb(255, 203, 139)">yes</span><span>
</span><span>   </span><span class="token key" style="color:rgb(173, 219, 103);font-style:italic">writable</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">=</span><span> </span><span class="token value" style="color:rgb(255, 203, 139)">yes</span><span>
</span><span>   </span><span class="token key" style="color:rgb(173, 219, 103);font-style:italic">guest ok</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">=</span><span> </span><span class="token value" style="color:rgb(255, 203, 139)">no</span><span>
</span><span>   </span><span class="token key" style="color:rgb(173, 219, 103);font-style:italic">read only</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">=</span><span> </span><span class="token value" style="color:rgb(255, 203, 139)">no</span><span>
</span><span>   </span><span class="token key" style="color:rgb(173, 219, 103);font-style:italic">valid users</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">=</span><span> </span><span class="token value" style="color:rgb(255, 203, 139)">alex, @sambausers</span><span>
</span><span>   </span><span class="token key" style="color:rgb(173, 219, 103);font-style:italic">create mask</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">=</span><span> </span><span class="token value" style="color:rgb(255, 203, 139)">0664</span><span>
</span><span>   </span><span class="token key" style="color:rgb(173, 219, 103);font-style:italic">directory mask</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">=</span><span> </span><span class="token value" style="color:rgb(255, 203, 139)">0775</span><span>
</span></code></pre></div>

**Após modificar, reinicie os serviços:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-uvzqvraq5" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> systemctl restart smbd nmbd
</span></code></pre></div>

---

## 👤 Gerenciamento de Usuários Samba

**Descrição:** Usuários que acessarão o compartilhamento Samba precisam existir no sistema Linux e ter uma senha Samba.

### 1. Criar Usuário Linux

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-wh7vgyv1e" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">useradd</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-m</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-s</span><span> /bin/bash alex
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">passwd</span><span> alex
</span></code></pre></div>

### 2. Adicionar Usuário ao Banco de Dados Samba

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-vkp9x8agx" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> smbpasswd </span><span class="token parameter" style="color:rgb(214, 222, 235)">-a</span><span> alex
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Digite a senha Samba (pode ser diferente da senha Linux)</span><span>
</span></code></pre></div>

### 3. Criar Grupo Samba (Opcional)

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-j5mnk86g5" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">groupadd</span><span> sambausers
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">usermod</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-aG</span><span> sambausers alex
</span></code></pre></div>

---

## 📁 Configuração de Diretório

**Descrição:** O diretório a ser compartilhado precisa ter as permissões corretas no Linux.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-1tr3e2igl" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Criar diretório</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">mkdir</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> /srv/samba/compartilhado
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Definir proprietário e grupo (ex: alex e sambausers)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">chown</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-R</span><span> alex:sambausers /srv/samba/compartilhado
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Definir permissões (ex: rwx para proprietário/grupo, r-x para outros)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">chmod</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-R</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">2775</span><span> /srv/samba/compartilhado
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># O &#x27;2&#x27; no início é o SGID, para que novos arquivos herdem o grupo &#x27;sambausers&#x27;</span><span>
</span></code></pre></div>

---

## 🌐 Acesso com Firewall

**Descrição:** Abrir as portas necessárias no firewall.

- **NetBIOS Name Service:** `137/udp`
- **NetBIOS Datagram Service:** `138/udp`
- **SMB/CIFS:** `139/tcp`
- **SMB/CIFS (direto):** `445/tcp`

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-9j6cdw68s" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-A</span><span> INPUT </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> udp </span><span class="token parameter" style="color:rgb(214, 222, 235)">--dport</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">137</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-j</span><span> ACCEPT
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-A</span><span> INPUT </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> udp </span><span class="token parameter" style="color:rgb(214, 222, 235)">--dport</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">138</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-j</span><span> ACCEPT
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-A</span><span> INPUT </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> tcp </span><span class="token parameter" style="color:rgb(214, 222, 235)">--dport</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">139</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-j</span><span> ACCEPT
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-A</span><span> INPUT </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> tcp </span><span class="token parameter" style="color:rgb(214, 222, 235)">--dport</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">445</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-j</span><span> ACCEPT
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Permitir conexões estabelecidas</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-A</span><span> INPUT </span><span class="token parameter" style="color:rgb(214, 222, 235)">-m</span><span> state </span><span class="token parameter" style="color:rgb(214, 222, 235)">--state</span><span> ESTABLISHED,RELATED </span><span class="token parameter" style="color:rgb(214, 222, 235)">-j</span><span> ACCEPT
</span></code></pre></div>

---

## 💻 Acesso do Cliente Windows

1. **Abrir Explorador de Arquivos.**
2. **Digitar:** `\\<IP_DO_SERVIDOR_LINUX>\Compartilhado`
3. **Autenticar:** Usar o nome de usuário e senha Samba.

---

## 📊 Logs

**Arquivos de log:**
- `/var/log/samba/log.smbd`
- `/var/log/samba/log.nmbd`
- `/var/log/samba/log.<hostname_cliente>`

**Visualizar logs em tempo real:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-m8qotvelz" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">tail</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-f</span><span> /var/log/samba/log.smbd
</span></code></pre></div>

---

## 🔗 Links Relacionados

- [[30_FTP-vsftpd]]
- [[16_SSH]]
- [[19_Hardening-Linux]]
- [[17_Firewall-iptables]]
- [[07_Gerenciamento-de-Usuarios]]
- [[08_Gerenciamento-de-Grupos]]

---

## 📚 Referências

- Samba Official: [www.samba.org](https://www.samba.org/)
- Samba Documentation: [www.samba.org/samba/docs](https://www.samba.org/samba/docs)
- Ubuntu Samba Server Guide: [ubuntu.com/server/docs/samba-file-server](https://ubuntu.com/server/docs/samba-file-server)
