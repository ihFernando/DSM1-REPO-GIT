# DSM1-REPO-GIT

Repositório utilizado para auxilio da aula de Design Digital + Desenvolvimento Web I da **Fatec São José dos Campos** para explicar na prática os conceitos de Git, versionamento de código e estratégias de branches.

---

## O que é Git?

Git é um sistema de controle de versão distribuído. Ele registra o histórico de alterações de arquivos ao longo do tempo, permitindo colaboração em equipe, rastreamento de mudanças e reversão a estados anteriores do projeto.

---

## Configuração inicial

Antes de usar o Git, configure sua identidade:

```bash
git config --global user.name "Seu Nome"
git config --global user.email "seu@email.com"
```

---

## Comandos essenciais

### Inicializar e clonar

| Comando           | Descrição                                        |
| ----------------- | ------------------------------------------------ |
| `git init`        | Inicializa um repositório Git na pasta atual     |
| `git clone <url>` | Clona um repositório remoto para a máquina local |

### Verificar estado e histórico

| Comando                     | Descrição                                                               |
| --------------------------- | ----------------------------------------------------------------------- |
| `git status`                | Exibe o estado atual dos arquivos (modificados, staged, não rastreados) |
| `git log`                   | Mostra o histórico de commits                                           |
| `git log --oneline --graph` | Histórico resumido com visualização de branches                         |
| `git diff`                  | Mostra as diferenças entre arquivos modificados e o último commit       |

### Adicionar e commitar

| Comando                    | Descrição                                         |
| -------------------------- | ------------------------------------------------- |
| `git add <arquivo>`        | Adiciona um arquivo à área de stage               |
| `git add .`                | Adiciona todos os arquivos modificados ao stage   |
| `git commit -m "mensagem"` | Registra as mudanças em stage como um novo commit |
| `git commit --amend`       | Corrige o último commit (mensagem ou arquivos)    |

### Branches

| Comando                    | Descrição                                               |
| -------------------------- | ------------------------------------------------------- |
| `git branch`               | Lista as branches locais                                |
| `git branch <nome>`        | Cria uma nova branch                                    |
| `git checkout <branch>`    | Muda para a branch informada                            |
| `git checkout -b <branch>` | Cria e muda para a nova branch                          |
| `git switch <branch>`      | Alternativa moderna ao `checkout` para trocar de branch |
| `git switch -c <branch>`   | Cria e muda para a nova branch (moderno)                |
| `git merge <branch>`       | Faz o merge da branch informada na branch atual         |
| `git branch -d <branch>`   | Deleta uma branch local (seguro)                        |

### Repositório remoto

| Comando                    | Descrição                                               |
| -------------------------- | ------------------------------------------------------- |
| `git remote -v`            | Lista os repositórios remotos configurados              |
| `git push origin <branch>` | Envia commits locais para o remoto                      |
| `git pull`                 | Baixa e integra as alterações do remoto na branch atual |
| `git fetch`                | Baixa as alterações do remoto sem integrar              |

### Desfazendo alterações

| Comando                          | Descrição                                                  |
| -------------------------------- | ---------------------------------------------------------- |
| `git restore <arquivo>`          | Descarta alterações não staged em um arquivo               |
| `git restore --staged <arquivo>` | Remove um arquivo da área de stage                         |
| `git revert <hash>`              | Cria um novo commit que desfaz um commit anterior          |
| `git reset --soft HEAD~1`        | Desfaz o último commit mantendo as alterações em stage     |
| `git reset --hard HEAD~1`        | Desfaz o último commit e descarta as alterações (cuidado!) |

---

## Workflow basico (fluxo de trabalho)

O ciclo de vida de uma alteracao no Git segue este fluxo:

```
Modificar arquivo  -->  git add  -->  git commit  -->  git push
  (working dir)        (staging)      (repositorio     (remoto)
                                        local)
```

### Passo a passo no dia a dia

```bash
# 1. Atualize sua branch local antes de comecar
git pull

# 2. Crie uma branch para a sua tarefa
git checkout -b feature/
ou
git switch -c feature/nome-da-funcionalidade

# 3. Faca suas alteracoes e registre com commits
git add .
git commit -m "feat: adiciona funcionalidade X"

# 4. Envie a branch para o remoto
git push origin feature/nome-da-funcionalidade

# 5. Abra um Pull Request para revisao e merge na branch principal
```

---

## Estrategia de branches

Neste repositorio usamos uma estrategia simplificada baseada no **GitHub Flow**, adequada para projetos de aula.

```
main
 |
 |---- feature/login
 |---- feature/cadastro
 |---- fix/correcao-validacao
```

### Tipos de branch

| Prefixo          | Uso                                                        |
| ---------------- | ---------------------------------------------------------- |
| `main`           | Branch principal, sempre estavel. Nao commitar diretamente |
| `feature/<nome>` | Nova funcionalidade                                        |
| `fix/<nome>`     | Correcao de bug                                            |
| `hotfix/<nome>`  | Correcao urgente em producao                               |
| `docs/<nome>`    | Atualizacao de documentacao                                |

### Regras

- Nunca commitar diretamente na `main`
- Toda mudanca entra via Pull Request (PR)
- O PR deve ser revisado por pelo menos um colega antes do merge
- Apagar a branch apos o merge (opcional)

---

## Boas praticas de commit

Use mensagens de commit claras e no seguinte formato:

```
<tipo>: <descricao curta no imperativo>
```

Exemplos:

```bash
git commit -m "feat: adiciona tela de login"
git commit -m "fix: corrige erro de validacao no formulario"
git commit -m "docs: atualiza README com instrucoes de setup"
git commit -m "refactor: extrai funcao de formatacao de datas"
```

Tipos comuns: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`

---

## Recursos para aprofundar

- Documentacao oficial: <https://git-scm.com/doc>
- Livro Pro Git (gratuito): <https://git-scm.com/book/pt-br/v2>
- Visualizador interativo de Git: <https://learngitbranching.js.org/?locale=pt_BR>

---

> Repositorio de apoio didatico — Fatec Sao Jose dos Campos | Curso DSM | 1º Semestre
