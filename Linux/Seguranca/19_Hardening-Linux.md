
# 🔒 Hardening de Sistemas Linux

> **Tags:** #linux #seguranca #hardening #best-practices #auditoria #firewall #permissoes

---

## 📌 Visão Geral

**Hardening** é o processo de proteger um sistema operacional, aplicação ou dispositivo, reduzindo sua superfície de ataque e minimizando vulnerabilidades.

🎯 **Objetivo:** Tornar o sistema Linux mais resiliente a ataques e mais seguro contra acessos não autorizados.

---

## 📊 Princípios de Hardening

### 1. Princípio do Menor Privilégio

**Descrição:** Conceder apenas as permissões e acessos estritamente necessários para usuários, processos e serviços.

---

### 2. Redução da Superfície de Ataque

**Descrição:** Desabilitar serviços desnecessários, remover software não utilizado e fechar portas não essenciais.

---

### 3. Defesa em Profundidade

**Descrição:** Implementar múltiplas camadas de segurança para que, se uma falhar, outras ainda protejam o sistema.

---

### 4. Auditoria e Monitoramento

**Descrição:** Registrar e revisar logs de segurança para detectar atividades suspeitas.

---

## ⚙️ Hardening do Sistema Operacional

### 1. Atualização e Patch Management

**Descrição:** Manter o sistema e todos os softwares atualizados para corrigir vulnerabilidades conhecidas.

bash
#### Debian/Ubuntu

sudo apt update && sudo apt upgrade -y
#### Red Hat/CentOS

sudo yum update -y

**Recomendação:** Configurar atualizações automáticas para patches de segurança.

---

### 2. Gerenciamento de Usuários e Senhas

**Descrição:** Implementar políticas de senha fortes e gerenciar contas de usuário de forma segura.

- **Desabilitar contas padrão não utilizadas:** `guest`, `ftp`, etc.
- **Bloquear contas inativas:** `sudo usermod -L <user>`
- **Excluir usuários desnecessários:** `sudo userdel -r <user>`
- **Políticas de senha:** [[21_Politicas-de-Senha]]

---

### 3. Permissões de Arquivos e Diretórios

**Descrição:** Configurar permissões adequadas para evitar acesso não autorizado a arquivos sensíveis.

- **Permissões mínimas:** `644` para arquivos, `755` para diretórios.
- **Arquivos sensíveis:** `600` para chaves SSH, `400` para arquivos de configuração críticos.
- **SUID/SGID:** Auditar e remover binários SUID/SGID desnecessários.

**Ver detalhes em:** [[05_Permissoes-Linux]]

---

### 4. Firewall

**Descrição:** Configurar um firewall para controlar o tráfego de rede.

- **Bloquear tudo por padrão:** `sudo iptables -P INPUT DROP`
- **Permitir apenas o essencial:** SSH (porta 22), HTTP/HTTPS (80/443).
- **Ver detalhes em:** [[17_Firewall-iptables]]

---

### 5. SSH Hardening

**Descrição:** Proteger o acesso remoto via SSH.

- **Desabilitar login root:** `PermitRootLogin no`
- **Autenticação por chave:** `PasswordAuthentication no`
- **Mudar porta padrão:** `Port 2222`
- **Limitar usuários:** `AllowUsers <user>`
- **Ver detalhes em:** [[16_SSH]]

---

### 6. Desabilitar Serviços Desnecessários

**Descrição:** Reduzir a superfície de ataque parando e desabilitando serviços não utilizados.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-mtpxcw6xr" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Listar serviços</span><span>
</span><span>systemctl list-units </span><span class="token parameter" style="color:rgb(214, 222, 235)">--type</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span>service </span><span class="token parameter" style="color:rgb(214, 222, 235)">--state</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span>running
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Parar serviço</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> systemctl stop </span><span class="token" style="color:rgb(127, 219, 202)">&lt;</span><span>service</span><span class="token" style="color:rgb(127, 219, 202)">&gt;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Desabilitar serviço no boot</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> systemctl disable </span><span class="token" style="color:rgb(127, 219, 202)">&lt;</span><span>service</span><span class="token" style="color:rgb(127, 219, 202)">&gt;</span><span>
</span></code></pre></div>

---

### 7. Auditoria e Logs

**Descrição:** Configurar o sistema para registrar eventos de segurança e revisar logs regularmente.

- **`auditd`:** Ferramenta para auditoria de eventos de segurança.
- **`journalctl`:** Visualizar logs do Systemd.
- **`logrotate`:** Gerenciar rotação de logs.
- **Ver detalhes em:** [[22_Auditoria-e-Logs]]

---

### 8. SELinux / AppArmor

**Descrição:** Mecanismos de controle de acesso obrigatório (MAC) para reforçar a segurança.

- **SELinux (Red Hat):** Define políticas de segurança granulares para processos e arquivos.
- **AppArmor (Ubuntu):** Define perfis de segurança para aplicações.

---

### 9. Proteção contra Brute Force (Fail2ban)

**Descrição:** Bloqueia IPs que tentam repetidamente acessar serviços (SSH, FTP, etc.).

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-7ojxv7uaa" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Instalar</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">apt</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">install</span><span> fail2ban
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Configurar (ex: /etc/fail2ban/jail.local)</span><span>
</span></code></pre></div>

---

### 10. Integridade de Arquivos (AIDE / Tripwire)

**Descrição:** Monitorar a integridade de arquivos críticos do sistema para detectar alterações não autorizadas.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-t9g4ib3vg" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Instalar AIDE</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">apt</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">install</span><span> aide aide-common
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Inicializar banco de dados</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> aide </span><span class="token parameter" style="color:rgb(214, 222, 235)">--init</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar integridade</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> aide </span><span class="token parameter" style="color:rgb(214, 222, 235)">--check</span><span>
</span></code></pre></div>

---

### 11. Limpeza de Arquivos Temporários

**Descrição:** Remover arquivos temporários que podem conter informações sensíveis.

- `/tmp`: Limpo no reboot.
- `/var/tmp`: Não limpo no reboot.

---

## 📊 Ferramentas de Hardening

### Lynis

**Descrição:** Ferramenta de auditoria de segurança para sistemas Unix-like.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-uvk7ncqqc" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Instalar</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">apt</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">install</span><span> lynis
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Rodar auditoria</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> lynis audit system
</span></code></pre></div>

---

### OpenSCAP

**Descrição:** Ferramenta para auditoria de conformidade com padrões de segurança (CIS Benchmarks, NIST).

---

## 🔗 Links Relacionados

- [[16_SSH]]
- [[17_Firewall-iptables]]
- [[05_Permissoes-Linux]]
- [[21_Politicas-de-Senha]]
- [[22_Auditoria-e-Logs]]
- [[20_ACL]]

---

## 📚 Referências

- CIS Benchmarks: [www.cisecurity.org/benchmarks](https://www.cisecurity.org/benchmarks)
- NIST SP 800-171: [csrc.nist.gov/publications/detail/sp/800-171/rev-2/final](https://csrc.nist.gov/publications/detail/sp/800-171/rev-2/final)
- Lynis: [cisofy.com/lynis](https://cisofy.com/lynis/)
- Fail2ban: [www.fail2ban.org](https://www.fail2ban.org/)