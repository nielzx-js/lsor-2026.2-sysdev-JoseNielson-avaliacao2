# 📑 Repositório Template: Avaliação 2 — LSOR - Técnico em Desenvolvimento de Sistemas (2026.02)

Este repositório é o modelo oficial para a realização e entrega da **Avaliação Prática II** da disciplina de **Laboratório de Sistemas Operacionais e Redes (LSOR)** do **Curso Técnico Integrado em Desenvolvimento de Sistemas** do IFAL - Campus Maceió.

A prova é **individual** e **prática**: você vai trabalhar em uma máquina virtual no VirtualBox e registrar cada tarefa com o comando executado, o print da tela e uma frase curta explicando o resultado. O conteúdo cobrado está nos roteiros das Aulas 01 a 05 do [repositório da disciplina](https://github.com/alaelson/labredes-2026.2-sysdev).

---

## 🚀 Instruções para o Aluno (Como Realizar a Prova)

### Passo 1: Criar o seu Repositório de Resposta
1. Entre na sua conta do GitHub.
2. Neste repositório do professor, clique no botão verde **"Use this template"** → **"Create a new repository"**.
3. Configure o seu novo repositório:
   * **Repository name:** `lsor-2026.2-sysdev-<nomedoaluno>-avaliacao2`
     (`<nomedoaluno>` em minúsculas, sem acentos nem espaços, com hífen se precisar. Ex.: `lsor-2026.2-sysdev-joao-silva-avaliacao2`)
   * **Visibility:** obrigatoriamente **Private** (Privado).
4. Depois de criar, vá em **Settings** → **Collaborators** → **Add people** e adicione o professor (`alaelson`) como colaborador. **Sem esse passo o professor não consegue corrigir a sua prova.**

### Passo 2: Obter e Configurar a Máquina Virtual
1. No laboratório, acesse o servidor de arquivos:
   * Caminho de rede: `\\172.20.20.21\public\avaliacao2`
   * Usuário: `alunoifal` | Senha: `alunoifal`
2. Copie o arquivo **`UbuntuAvaliacao2.ova`** para a sua pasta de trabalho: `C:\2026.2\SysDevTech\VM\<NomeDoAluno>`.
3. Importe a VM no VirtualBox (detalhes na Questão 1).
4. Credenciais da VM: Usuário: `administrador` | Senha: `adminifal`.

### Passo 3: Responder a Avaliação
1. No seu repositório, abra o arquivo **`Avaliacao2.md`**. É nele que você responde.
2. Edite pelo próprio site do GitHub (botão de lápis) ou clone o repositório na máquina do laboratório.
3. Para **cada questão**, registre:
   * o **bloco de código** com os comandos exatamente como você digitou;
   * o **print** da tela mostrando o comando e a saída (o prompt, por exemplo `administrador@...` ou `ana@...`, deve aparecer);
   * **uma ou duas frases** dizendo o que a saída mostra e se era o esperado.
4. Salve os prints na pasta **`prints/`**, com nomes `qN_descricao.png` (minúsculas, sem espaços nem acentos), e referencie com caminho relativo: `![Questão 4](prints/q4_usuarios.png)`.

> 💡 **Dica:** a partir da Questão 3 você pode fazer a prova pelo **SSH** no PowerShell. Fica mais fácil copiar comandos e saídas para o Markdown.

### Passo 4: Envio Oficial
1. Confira se o `Avaliacao2.md` e todos os prints da pasta `prints/` foram enviados (commit) para o seu repositório.
2. Abra o arquivo `Avaliacao2.md` no GitHub e copie o **link direto** dele.
3. Envie esse link no formulário indicado pelo professor (Google Classroom / Google Forms) dentro do prazo.

---

## 📁 Estrutura Esperada do Repositório do Aluno

```text
lsor-2026.2-sysdev-<nomedoaluno>-avaliacao2/
├── README.md               # Este arquivo de instruções
├── Avaliacao2.md           # Seu caderno de respostas (preenchido)
└── prints/                 # Capturas de tela das evidências
    ├── q1_vm_importada.png
    ├── q2_ip_addr.png
    ├── q3_netstat_listening.png
    ├── q4_usuarios.png
    └── ... (demais capturas exigidas)
```

---

_Boa prova!_  
**Prof. Alaelson Jatobá**  
_alaelson@ifal.edu.br_
