# 📑 CADERNO DE RESPOSTAS: AVALIAÇÃO PRÁTICA II
## Disciplina: Laboratório de Sistemas Operacionais e Redes (LSOR)
**Professor:** Alaelson Jatobá  
**Semestre Letivo:** 2026.02  
**Curso:** Técnico Integrado em Desenvolvimento de Sistemas  

---

## 👤 Identificação do Aluno
*   **Nome Completo:** [Preencha aqui seu nome]
*   **Matrícula:** [Preencha aqui sua matrícula]
*   **Seu usuário na VM (Questão 4):** [ex.: joaosilva]
*   **Link do seu Repositório no GitHub:** [Preencha aqui o link]
*   **Data de Realização:** [Preencha aqui a data]

---

## 🚨 Instruções Gerais

1.  **Prova individual.** Cada aluno trabalha na sua própria VM e no seu próprio repositório privado.
2.  **Como responder cada questão:** em todo campo **"Sua resposta"**, coloque, nesta ordem:
    1. o **bloco de código** com os comandos exatamente como você digitou;
    2. o **print** da tela, salvo em `prints/` e referenciado no Markdown (ex.: `![Q4](prints/q4_usuarios.png)`). O prompt (`administrador@...`, `ana@...`) precisa aparecer no print;
    3. **uma ou duas frases** dizendo o que a saída mostra e se era o esperado.
3.  **Use `sudo` só quando o comando alterar o sistema** (criar usuários, grupos, pastas do sistema, mudar donos e permissões).
4.  **Prints de outro colega anulam a questão.** O nome da sua VM e o seu usuário pessoal aparecem nas telas, então cada evidência precisa ser sua.

---

## ✏️ Guia Rápido do Editor `nano`

O `nano` é o editor de texto usado nas Questões 8, 9 e 10. Ele abre dentro do próprio terminal.

**Abrir (ou criar) um arquivo:**
```bash
nano nome_do_arquivo.txt
```
Se o arquivo não existir, o `nano` abre uma tela vazia e o arquivo é criado quando você salvar.

**Teclas principais** (no rodapé do `nano`, o símbolo `^` significa a tecla **Ctrl**, e `M-` significa **Alt**):

| Ação | Teclas | O que acontece |
| :--- | :--- | :--- |
| Escrever | digite normalmente | Use as **setas** do teclado para mover o cursor. Não funciona clicar com o mouse. |
| **Salvar** | **`Ctrl + O`** e depois **`Enter`** | O `nano` mostra o nome do arquivo no rodapé; o `Enter` confirma. Aparece a mensagem `Wrote N lines`. |
| **Sair** | **`Ctrl + X`** | Fecha o editor e volta ao terminal. |
| Sair sem ter salvo | **`Ctrl + X`** → **`Y`** → **`Enter`** | O `nano` pergunta `Save modified buffer?`. **`Y`** (yes) salva e **`N`** (no) descarta as alterações. |
| Cancelar uma pergunta | **`Ctrl + C`** | Volta para a edição sem salvar nem sair. |
| Apagar a linha inteira | **`Ctrl + K`** | Recorta a linha onde está o cursor. |
| Colar | **`Ctrl + U`** | Cola a última linha recortada. |

**Resumo para não errar:** escreva → **`Ctrl + O`**, **`Enter`** (salva) → **`Ctrl + X`** (sai) → confira com **`cat nome_do_arquivo.txt`**.

> ⚠️ **Se aparecer `Permission denied` ao salvar**, o usuário atual não pode gravar naquela pasta. Saia com **`Ctrl + X`** → **`N`**, confira **quem você é** (`whoami`) e **onde está salvando** (`pwd`), e tente de novo.
>
> 💡 **Pelo SSH no PowerShell**, você pode colar um texto copiado do Windows dentro do `nano` com o **botão direito do mouse**.

---

## 🏆 Cenário da Prova: Hackathon IFAL

Você é o responsável pela infraestrutura do **Hackathon IFAL**. O servidor do evento precisa ter contas para os participantes, grupos por equipe e pastas em que cada equipe só acessa o seu próprio material.

| Usuário | Senha | Equipe (grupo) |
| :--- | :--- | :--- |
| `ana` | `ana2026` | `equipe-web` |
| `bruno` | `bruno2026` | `equipe-web` |
| `carla` | `carla2026` | `equipe-mobile` |
| `visitante` | `visitante2026` | *(nenhuma)* |
| **`<seunome>`** | **`<seunome>2026`** | **`equipe-web` e `equipe-mobile`** (coordenador) |

> **`<seunome>`** é o seu primeiro nome seguido do sobrenome, tudo em minúsculas, sem acentos e sem espaços. Exemplo: João Silva → usuário `joaosilva`, senha `joaosilva2026`.

---

## 📋 Questões

### 💻 QUESTÃO 1: Importação da VM no VirtualBox

1.  Copie `UbuntuAvaliacao2.ova` de `\\172.20.20.21\public\avaliacao2` (usuário/senha `alunoifal`) para `C:\2026.2\SysDevTech\VM\<NomeDoAluno>`.
2.  No VirtualBox, use **Arquivo → Importar Appliance**. Na tela de configurações da importação:
    *   altere o **Nome** da VM para **`avaliacao2-<seunome>`** (ex.: `avaliacao2-joaosilva`);
    *   altere a **Pasta Base da Máquina** para `C:\2026.2\SysDevTech\VM\<NomeDoAluno>`.
3.  Antes de ligar, abra **Configurações** da VM e confira: **768 MB** de memória, **1 CPU** e **Adaptador 1 em NAT**.
4.  *(Recomendado)* Tire um snapshot chamado **`inicio`** para poder voltar ao estado inicial se algo der errado.
5.  Inicie a VM e faça login com `administrador` / `adminifal`.

> **🖼️ PRINTS:** `q1_vm_importada.png` mostrando a janela do VirtualBox com a VM `avaliacao2-<seunome>` (memória e CPU à vista) e o console da VM com o login feito.

*   **Sua resposta:**
    [Substitua este texto pelos passos realizados, os prints e a sua frase de interpretação]

---

### 🌐 QUESTÃO 2: Diagnóstico da Rede da VM (NAT)

1.  Mostre as interfaces, os endereços e a rota padrão da VM:
    ```bash
    ip addr show
    ip route
    ```
2.  Preencha a tabela abaixo com os valores da **sua** VM:

    | Interface | IP / prefixo | Endereço MAC | Gateway padrão |
    | :--- | :--- | :--- | :--- |
    | | | | |

3.  Faça os testes de conectividade em camadas, do mais próximo ao mais distante:
    ```bash
    ping -c 4 127.0.0.1
    ping -c 4 10.0.2.2
    ping -c 4 8.8.8.8
    ping -c 4 google.com
    ```

> **🖼️ PRINTS:** `q2_ip_addr.png` (saída de `ip addr show` e `ip route`) e `q2_ping.png` (os testes de `ping`).

*   **Sua resposta:**
    [Comandos, tabela preenchida, prints e interpretação. Se algum ping falhar, diga em qual camada está o problema.]

---

### 🔐 QUESTÃO 3: Acesso Remoto por SSH com Redirecionamento de Portas

1.  No **PowerShell do Windows**, mostre que a porta `5222` ainda não está em uso:
    ```powershell
    netstat -an | findstr 5222
    ```
2.  No VirtualBox, em **Configurações → Rede → Adaptador 1 (NAT) → Avançado → Redirecionamento de Portas**, crie a regra:

    | Nome | Protocolo | IP do Hospedeiro | Porta do Hospedeiro | IP do Convidado | Porta do Convidado |
    | :--- | :---: | :---: | :---: | :---: | :---: |
    | SSH | TCP | 127.0.0.1 | 5222 | 10.0.2.15 | 22 |

3.  Repita o `netstat -an | findstr 5222` e mostre a porta em `LISTENING`.
4.  Conecte na VM pelo PowerShell:
    ```powershell
    ssh -p 5222 administrador@127.0.0.1
    ```
5.  Dentro da sessão SSH, execute `w` e mostre a sessão `pts/0`.

> **🖼️ PRINTS:** `q3_netstat_antes.png`, `q3_regra_virtualbox.png`, `q3_netstat_listening.png` e `q3_ssh_w.png`.

*   **Sua resposta:**
    [Comandos, prints e interpretação]

---

### 👥 QUESTÃO 4: Criação dos Usuários

1.  Crie os cinco usuários da tabela do cenário com o `adduser`, usando as senhas indicadas:
    ```bash
    sudo adduser ana
    sudo adduser bruno
    sudo adduser carla
    sudo adduser visitante
    sudo adduser <seunome>
    ```
2.  Confira as contas criadas:
    ```bash
    tail -n 5 /etc/passwd
    ```

> **🖼️ PRINTS:** `q4_adduser.png` (criação do **seu** usuário) e `q4_usuarios.png` (saída do `tail`).

*   **Sua resposta:**
    [Comandos, prints e interpretação]

---

### 🧑‍🤝‍🧑 QUESTÃO 5: Grupos das Equipes

1.  Crie os grupos `equipe-web` e `equipe-mobile`.
2.  Adicione os usuários conforme a tabela do cenário, usando `usermod -aG`. Lembre que **`<seunome>` entra nos dois grupos** e que `visitante` não entra em nenhum.
3.  Confira o resultado:
    ```bash
    id ana
    id carla
    id visitante
    id <seunome>
    getent group equipe-web equipe-mobile
    ```

> **🖼️ PRINTS:** `q5_grupos.png` mostrando os comandos de criação/associação e as saídas do `id` e do `getent`.

*   **Sua resposta:**
    [Comandos, prints e interpretação]

---

### 📂 QUESTÃO 6: Estrutura de Diretórios (FHS) e Pastas do Evento

1.  Mostre as pastas da raiz do sistema e confirme que `/bin` e `/sbin` são links simbólicos:
    ```bash
    cd /
    ls
    ls -ld /bin /sbin
    ```
2.  Pelo padrão FHS, dados de serviços oferecidos pelo servidor ficam em `/srv`. Crie a estrutura do evento **com um único comando**:
    ```bash
    sudo mkdir -p /srv/hackathon/web/codigo /srv/hackathon/mobile/telas
    ```
3.  Mostre a árvore criada:
    ```bash
    cd /srv/hackathon
    ls -R
    ```

> **🖼️ PRINTS:** `q6_fhs.png` (raiz e links simbólicos) e `q6_mkdir_ls_r.png` (árvore criada).

*   **Sua resposta:**
    [Comandos, prints e interpretação]

---

### 🔒 QUESTÃO 7: Donos e Permissões das Pastas

1.  Mostre os donos e permissões **antes** da mudança:
    ```bash
    ls -ld /srv/hackathon/web /srv/hackathon/mobile
    ```
2.  Faça com que:
    *   `/srv/hackathon/web` (e o que estiver dentro) pertença ao usuário `administrador` e ao grupo `equipe-web`;
    *   `/srv/hackathon/mobile` (e o que estiver dentro) pertença ao usuário `administrador` e ao grupo `equipe-mobile`;
    *   nas duas pastas, dono e grupo tenham **controle total** e os outros usuários **nenhum acesso** (permissão numérica, aplicada também às subpastas).
3.  Mostre o resultado **depois** com `ls -ld`.
4.  Crie o arquivo `/srv/hackathon/web/codigo/README.txt`, com dono `administrador`, grupo `equipe-web` e **leitura e escrita só para dono e grupo**. Mostre com `ls -l`.

> **🖼️ PRINTS:** `q7_antes_depois.png` (com os comandos `chown`/`chmod` e o `ls -ld` antes e depois) e `q7_readme_660.png`.

*   **Sua resposta:**
    [Comandos, prints e interpretação]

---

### 📝 QUESTÃO 8: Ficha de Inscrição de Cada Participante (`su -`)

1.  Entre como cada participante usando **`su -`** e crie, na pasta pessoal dele, o arquivo **`inscricao.txt`** no formato JSON abaixo (use o `nano`). *(Para salvar: `Ctrl + O`, `Enter`. Para sair: `Ctrl + X`. Veja o **Guia Rápido do `nano`** no início da prova.)*
    ```bash
    su - ana
    nano ~/inscricao.txt
    cat ~/inscricao.txt
    pwd
    exit
    ```
    **Modelo do arquivo `inscricao.txt`:**
    ```json
    {
      "participante": "NOME",
      "equipe": "EQUIPE",
      "linguagem": "LINGUAGEM"
    }
    ```
    Preencha assim:
    *   `ana`: `"participante": "ANA"`, `"equipe": "equipe-web"`, `"linguagem": "JavaScript"`
    *   `bruno`: `"participante": "BRUNO"`, `"equipe": "equipe-web"`, `"linguagem": "PHP"`
    *   `carla`: `"participante": "CARLA"`, `"equipe": "equipe-mobile"`, `"linguagem": "Kotlin"`
    *   `<seunome>`: `"participante": "<SEU NOME COMPLETO>"`, `"equipe": "coordenacao"`, `"linguagem": "<sua linguagem favorita>"`

2.  Mostre a diferença entre `su` e `su -`. Como `administrador`, a partir da pasta `/srv/hackathon`, execute:
    ```bash
    cd /srv/hackathon
    su ana
    pwd
    exit
    su - ana
    pwd
    exit
    ```

> **🖼️ PRINTS:** `q8_inscricao.png` (a ficha do **seu** usuário com `cat` e `pwd`) e `q8_su_x_su_hifen.png` (os dois `pwd` diferentes).

*   **Sua resposta:**
    [Comandos, prints e interpretação. Diga em uma frase por que os dois `pwd` deram resultados diferentes.]

---

### 🕵️ QUESTÃO 9: Testes de Isolamento entre as Equipes

Usando sempre **`su -`**, execute os testes abaixo e mostre o resultado de cada um:

| Teste | Usuário | Ação | Resultado esperado |
| :---: | :--- | :--- | :--- |
| A | `ana` | `cd /srv/hackathon/web`, abrir `nano codigo/README.txt`, acrescentar a linha `Revisado por Ana`, salvar (`Ctrl + O`, `Enter`), sair (`Ctrl + X`) e mostrar com `cat codigo/README.txt` | Permitido |
| B | `ana` | `cd /srv/hackathon/mobile` | `Permission denied` |
| C | `visitante` | `cd /srv/hackathon/web` e `cd /srv/hackathon/mobile` | `Permission denied` nas duas |
| D | `<seunome>` | `cd /srv/hackathon/web` e `cd /srv/hackathon/mobile`, com `ls` em cada uma | Permitido nas duas |

> **🖼️ PRINTS:** `q9_teste_a.png`, `q9_teste_b.png`, `q9_teste_c.png` e `q9_teste_d.png`. O prompt do usuário precisa aparecer em cada print.

*   **Sua resposta:**
    [Comandos, prints e, para cada teste, uma frase explicando por que o acesso foi permitido ou negado]

---

### 📋 QUESTÃO 10: Lista de Inscritos, Permissões do Arquivo e Filtros de Linhas

A coordenação precisa de uma lista com todos os inscritos, que só a equipe web pode consultar.

1.  Como `administrador`, mostre as fichas criadas na Questão 8. É preciso `sudo` porque as pastas pessoais dos outros usuários são protegidas:
    ```bash
    sudo cat /home/ana/inscricao.txt
    sudo cat /home/bruno/inscricao.txt
    sudo cat /home/carla/inscricao.txt
    sudo cat /home/<seunome>/inscricao.txt
    ```
2.  Com o `nano`, crie o arquivo `/srv/hackathon/web/inscritos.txt` com o conteúdo abaixo, usando os dados das fichas (uma linha por participante). *(Para salvar: `Ctrl + O`, `Enter`. Para sair: `Ctrl + X`. Veja o **Guia Rápido do `nano`** no início da prova.)*
    ```bash
    nano /srv/hackathon/web/inscritos.txt
    ```
    ```text
    LISTA DE INSCRITOS - HACKATHON IFAL 2026
    Gerada por: <SEU NOME COMPLETO> - Data: <data de hoje>
    ==========================================
    ANA - equipe-web - JavaScript
    BRUNO - equipe-web - PHP
    CARLA - equipe-mobile - Kotlin
    <SEU NOME COMPLETO> - coordenacao - <sua linguagem favorita>
    ```
3.  Mostre o arquivo completo com `cat` e use os filtros de linhas para mostrar **só o cabeçalho** (3 primeiras linhas) e **só os 2 últimos inscritos**:
    ```bash
    cat /srv/hackathon/web/inscritos.txt
    head -n 3 /srv/hackathon/web/inscritos.txt
    tail -n 2 /srv/hackathon/web/inscritos.txt
    ```
4.  Mostre as permissões do arquivo com `ls -l` **antes** e **depois** de fazer com que ele pertença ao usuário `administrador` e ao grupo `equipe-web`, com **leitura e escrita só para dono e grupo** (permissão numérica).
5.  Teste o acesso com `su -`:
    *   `bruno` executa `cat /srv/hackathon/web/inscritos.txt` → deve funcionar;
    *   `carla` executa `cat /srv/hackathon/web/inscritos.txt` → deve dar `Permission denied`.

> **🖼️ PRINTS:** `q10_fichas.png` (os `sudo cat`), `q10_nano.png` (o arquivo aberto no `nano`), `q10_head_tail.png` (o `cat`, o `head` e o `tail`), `q10_permissoes.png` (`ls -l` antes e depois) e `q10_teste_bruno_carla.png`.

*   **Sua resposta:**
    [Comandos, prints e interpretação. Diga em uma frase por que `bruno` consegue ler a lista e `carla` não.]

---
*Fim da Avaliação. Confira se o `Avaliacao2.md` e todos os prints da pasta `prints/` estão no seu repositório e envie o link direto deste arquivo no formulário indicado pelo professor, dentro do prazo.*
