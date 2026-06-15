
# 🐧 Introdução ao Linux

> **Tags:** #linux #fundamentos #historia #open-source #gnu

---

## 📌 Visão Geral

**Linux** é um sistema operacional de código aberto baseado no kernel desenvolvido por **Linus Torvalds** em 1991.

🎯 **Objetivo:** Sistema operacional livre, estável e seguro para servidores, desktops e dispositivos embarcados.

---

## 📜 História

### Unix (1960-1970)

**Desenvolvido por:** AT&T Bell Labs
- Ken Thompson e Dennis Ritchie
- Escrito em linguagem C
- Base para sistemas modernos

**Referências:**
- [História do Unix (Wikipedia)](https://en.wikipedia.org/wiki/History_of_Unix)
- [Unix History (YouTube)](https://www.youtube.com/watch?v=5_EvsDPSdSM)

---

### GNU (1983)

**Criado por:** Richard Stallman

**Objetivo:** Criar sistema operacional livre compatível com Unix

**GNU:** GNU's Not Unix

**Componentes:**
- GCC (GNU Compiler Collection)
- Bash (Bourne Again Shell)
- Coreutils (comandos básicos)
- GRUB (bootloader)

**Site:** [gnu.org](https://www.gnu.org/)

---

### Linux (1991)

**Criado por:** Linus Torvalds (estudante finlandês)

**Primeira versão:** 0.01 (17 de setembro de 1991)

**Anúncio histórico:**

"I'm doing a (free) operating system (just a hobby, won't be big and professional like gnu) for 386(486) AT clones."

- Linus Torvalds, 25 de agosto de 1991

**Kernel oficial:** [kernel.org](https://www.kernel.org/)

---

### Debate Tanenbaum vs Torvalds

**Andrew Tanenbaum** (criador do MINIX) criticou a arquitetura monolítica do Linux.

**Linus Torvalds** defendeu sua escolha por performance.

**Referência:** [Debate Tanenbaum-Torvalds (Wikipedia)](https://pt.wikipedia.org/wiki/Debate_entre_Tanenbaum_e_Torvalds)

---

## 🐧 O que é Linux?

**Linux** é na verdade o **kernel** (núcleo do sistema operacional).

**GNU/Linux** é o sistema operacional completo:
- **Kernel:** Linux
- **Utilitários:** GNU
- **Interface gráfica:** X.org, Wayland
- **Desktop Environment:** GNOME, KDE, XFCE, Cinnamon

---

## 📊 Distribuições Linux

**Distribuição (Distro):** Conjunto de software empacotado com o kernel Linux.

### Principais Famílias

#### 1️⃣ Debian
**Gerenciador de pacotes:** APT/DPKG

**Distribuições baseadas:**
- Ubuntu
- Linux Mint
- Kali Linux
- Parrot OS

---

#### 2️⃣ Red Hat
**Gerenciador de pacotes:** YUM/DNF/RPM

**Distribuições baseadas:**
- Fedora
- CentOS
- Rocky Linux
- AlmaLinux

---

#### 3️⃣ Arch
**Gerenciador de pacotes:** Pacman

**Distribuições baseadas:**
- Manjaro
- EndeavourOS

---

#### 4️⃣ SUSE
**Gerenciador de pacotes:** Zypper

**Distribuições:**
- openSUSE
- SUSE Linux Enterprise

---

### Rolling Release vs Fixed Release

**Fixed Release:**
- Versões estáveis lançadas periodicamente
- Exemplo: Ubuntu 24.04 LTS

**Rolling Release:**
- Atualizações contínuas
- Sempre na versão mais recente
- Exemplo: Arch Linux, Manjaro

---

### Distribuições Mais Populares

**Ranking:** [distrowatch.com](https://distrowatch.com/)

**Top 5 (2024):**
1. Linux Mint
2. Ubuntu
3. Debian
4. Fedora
5. Pop!_OS

---

## 🆓 Licença e Filosofia

### GPL (GNU General Public License)

**Princípios:**
- ✅ Liberdade de **usar** o software
- ✅ Liberdade de **estudar** o código
- ✅ Liberdade de **modificar** o código
- ✅ Liberdade de **distribuir** cópias

**Copyleft:** Modificações devem manter a mesma licença.

---

### Open Source vs Free Software

| Aspecto | Free Software | Open Source |
|---------|---------------|-------------|
| **Foco** | Liberdade e ética | Praticidade e qualidade |
| **Filosofia** | Ideológica | Pragmática |
| **Organização** | FSF (Free Software Foundation) | OSI (Open Source Initiative) |

---

## 🌐 Linux Foundation

**Organização:** Promove o desenvolvimento do Linux e projetos open source.

**Site:** [linuxfoundation.org](https://www.linuxfoundation.org/)

**Projetos:**
- Linux Kernel
- Kubernetes
- Node.js
- Let's Encrypt

---

## 🖥️ Ambientes Gráficos

### Desktop Environments (DE)

| DE | Descrição | Recursos |
|----|-----------|----------|
| **GNOME** | Moderno e minimalista | Alto consumo de RAM |
| **KDE Plasma** | Personalizável e bonito | Médio consumo |
| **XFCE** | Leve e rápido | Baixo consumo |
| **Cinnamon** | Similar ao Windows | Médio consumo |
| **MATE** | Fork do GNOME 2 | Baixo consumo |

---

### Instalar Cinnamon (exemplo)

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-zkr9ybso2" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">apt</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">install</span><span> cinnamon-desktop-environment
</span></code></pre></div>

---

## 🔗 Links Relacionados

- [[Comandos-Basicos]]
- [[02_Estrutura-de-Diretorios]]
- [[Gerenciamento-de-Pacotes]]
- [[Distribuicoes-Linux]]

---

## 📚 Referências

- Linux Foundation: [linuxfoundation.org](https://www.linuxfoundation.org/)
- Kernel.org: [kernel.org](https://www.kernel.org/)
- GNU: [gnu.org](https://www.gnu.org/)
- FSF Directory: [directory.fsf.org](https://directory.fsf.org/wiki/Main_Page)
- Viva o Linux: [vivaolinux.com.br](https://www.vivaolinux.com.br/linux/)