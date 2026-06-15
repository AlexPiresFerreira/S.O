
# 🔑 Políticas de Senha no Linux

> **Tags:** #linux #seguranca #senhas #politicas #pam #pwquality #chage

---

## 📌 Visão Geral

Políticas de senha fortes são cruciais para a segurança de qualquer sistema, protegendo contra ataques de força bruta e dicionário.

🎯 **Objetivo:** Implementar e gerenciar políticas de senha robustas no Linux.

---

## 📊 Conceitos

### Força da Senha

**Descrição:** Medida da resistência de uma senha a ataques de adivinhação.

**Fatores:**
- Comprimento (mínimo de 12-16 caracteres).
- Complexidade (letras maiúsculas/minúsculas, números, símbolos).
- Aleatoriedade (evitar palavras de dicionário, datas, nomes).

---

### Envelhecimento da Senha (Password Aging)

**Descrição:** Força os usuários a mudar suas senhas periodicamente.

---

### Histórico de Senhas

**Descrição:** Impede que os usuários reutilizem senhas antigas.

---

## 🛠️ Ferramentas de Gerenciamento

### 1️⃣ chage (Change User Password Expiration Information)

**Descrição:** Exibe e modifica as informações de envelhecimento da senha.

**Sintaxe:** `sudo chage [opções] <username>`

**Opções Comuns:**
- `-l`: Listar informações de envelhecimento.
- `-E <YYYY-MM-DD>`: Definir data de expiração da conta.
- `-I <days>`: Definir dias de inatividade após a expiração da senha.
- `-m <days>`: Definir número mínimo de dias entre mudanças de senha.
- `-M <days>`: Definir número máximo de dias entre mudanças de senha.
- `-W <days>`: Definir número de dias de aviso antes da expiração.

**Exemplos:**

bash
#### Listar informações de senha do usuário

chage -l usuario
#### Forçar usuário a mudar senha no próximo login

sudo chage -d 0 usuario
#### Definir senha para expirar em 90 dias, aviso 7 dias antes, mínimo 5 dias

sudo chage -M 90 -W 7 -m 5 usuario

#### Definir conta para expirar em 2026-12-31

sudo chage -E 2026-12-31 usuario

---

### 2️⃣ /etc/login.defs

**Descrição:** Arquivo de configuração que define políticas padrão para novos usuários e senhas.

**Parâmetros importantes:**
- `PASS_MAX_DAYS`: Máximo de dias para a senha ser válida.
- `PASS_MIN_DAYS`: Mínimo de dias antes que a senha possa ser alterada.
- `PASS_WARN_AGE`: Dias de aviso antes da expiração.
- `ENCRYPT_METHOD`: Método de criptografia de senha (ex: SHA512).
- `UMASK`: Permissões padrão para novos arquivos/diretórios.

**Exemplo:**
```

# /etc/login.defs

PASS_MAX_DAYS 90 PASS_MIN_DAYS 7 PASS_WARN_AGE 14 ENCRYPT_METHOD SHA512

```
---

### 3️⃣ PAM (Pluggable Authentication Modules)

**Descrição:** Framework flexível que permite configurar módulos de autenticação.

**Localização:** `/etc/pam.d/`

**Módulos PAM importantes para senhas:**
- `pam_pwquality.so`: Impõe requisitos de qualidade de senha.
- `pam_unix.so`: Gerencia senhas Unix tradicionais.
- `pam_cracklib.so` (legado): Verifica a força da senha.
- `pam_pwhistory.so`: Impede reutilização de senhas.

---

#### Configurando `pam_pwquality` (Debian/Ubuntu)

**Instalação:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-1ah3mggs1" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">apt</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">install</span><span> libpam-pwquality
</span></code></pre></div>

**Arquivo de configuração:** `/etc/pam.d/common-password`

**Linha de configuração (exemplo):**
```

password requisite pam_pwquality.so retry=3 minlen=12 dcredit=-1 ucredit=-1 ocredit=-1 lcredit=-1 reject_username enforce_for_root

```
**Parâmetros de `pam_pwquality.so`:**
- `retry=<num>`: Número de tentativas.
- `minlen=<num>`: Comprimento mínimo da senha.
- `dcredit=<num>`: Mínimo de dígitos (`-1` = pelo menos 1 dígito).
- `ucredit=<num>`: Mínimo de maiúsculas (`-1` = pelo menos 1 maiúscula).
- `lcredit=<num>`: Mínimo de minúsculas (`-1` = pelo menos 1 minúscula).
- `ocredit=<num>`: Mínimo de outros caracteres (`-1` = pelo menos 1 símbolo).
- `reject_username`: Não permitir que a senha contenha o nome de usuário.
- `enforce_for_root`: Aplicar a política também para o root.
- `maxrepeat=<num>`: Máximo de caracteres repetidos.
- `badwords=<file>`: Lista de palavras proibidas.

---

#### Configurando `pam_pwhistory` (Histórico de Senhas)

**Arquivo de configuração:** `/etc/pam.d/common-password`

**Linha de configuração (exemplo):**
```

password [success=1 default=ignore] pam_unix.so obscure use_authtok try_first_pass sha512 password requisite pam_pwhistory.so remember=5 retry=3

```
**Parâmetros de `pam_pwhistory.so`:**
- `remember=<num>`: Número de senhas anteriores a serem lembradas.
- `retry=<num>`: Número de tentativas.

---

## 🔑 Implementando uma Política de Senha Forte

### 1. Comprimento Mínimo

- **`pam_pwquality.so`:** `minlen=12` (ou mais)
- **`/etc/login.defs`:** `PASS_MIN_LEN` (para `useradd`)

---

### 2. Complexidade

- **`pam_pwquality.so`:** `dcredit=-1 ucredit=-1 lcredit=-1 ocredit=-1`

---

### 3. Envelhecimento da Senha

- **`/etc/login.defs`:** `PASS_MAX_DAYS=90`, `PASS_MIN_DAYS=7`, `PASS_WARN_AGE=14`
- **`chage`:** Para usuários existentes (`sudo chage -M 90 -W 7 -m 7 <user>`)

---

### 4. Histórico de Senhas

- **`pam_pwhistory.so`:** `remember=5` (lembrar as últimas 5 senhas)

---

### 5. Bloqueio de Conta

- **`pam_tally2.so` ou `pam_faillock.so`:** Bloquear conta após N tentativas falhas de login.

**Exemplo (`/etc/pam.d/common-auth`):**
```

auth required pam_faillock.so preauth audit deny=3 unlock_time=600 auth [success=1 default=bad] pam_unix.so try_first_pass auth required pam_faillock.so authfail audit deny=3 unlock_time=600

```
- `deny=3`: Bloquear após 3 falhas.
- `unlock_time=600`: Desbloquear após 600 segundos (10 minutos).

---

## 🔗 Links Relacionados

- [[07_Gerenciamento-de-Usuarios]]
- [[19_Hardening-Linux]]
- [[22_Auditoria-e-Logs]]
- [[05_Permissoes-Linux]]

---

## 📚 Referências

- Chage Man Page: [man7.org/linux/man-pages/man1/chage.1.html](https://man7.org/linux/man-pages/man1/chage.1.html)
- Login.defs Man Page: [man7.org/linux/man-pages/man5/login.defs.5.html](https://man7.org/linux/man-pages/man5/login.defs.5.html)
- PAM Man Page: [man7.org/linux/man-pages/man8/pam.8.html](https://man7.org/linux/man-pages/man8/pam.8.html)
- Pwquality.conf Man Page: [man7.org/linux/man-pages/man5/pwquality.conf.5.html](https://man7.org/linux/man-pages/man5/pwquality.conf.5.html)
