# Workflow de Desenvolvimento

## Modelo de Workflow

**Modelo Adotado:** GitHub Flow

Uma branch principal (`main`) sempre pronta para produção. 

**Vantagens:**
- Simples e direto para times de qualquer tamanho
- Uma única branch principal sempre estável
- Fácil integração contínua
- Ideal para projetos com iterações rápidas

**Fluxo Visual:**
```
main (branch principal - sempre estável)
  ↓
  ├─ feature/nova-funcionalidade
  ├─ bugfix/corrigir-erro
  ├─ docs/atualizar-readme
  ├─ style/refatoracao-css
  └─ hotfix/correcao-critica
```

---

## Estratégia de Branches

### Nomenclatura

**Padrão:** `[tipo]/[descricao-em-kebab-case]`

### Tipos de Branch

| Tipo | Origem | Destino | Exemplo | Descrição |
|------|--------|---------|---------|-----------|
| `feature/` | main | main | `feature/homepage` | Novas funcionalidades |
| `bugfix/` | main | main | `bugfix/nav-menu` | Correção de bugs |
| `docs/` | main | main | `docs/api-guide` | Documentação |
| `style/` | main | main | `style/global-css` | Refatoração visual e código |
| `hotfix/` | main | main | `hotfix/critical-error` | Correções críticas urgentes |

### Exemplos 

- `feature/adicionar-galeria-imagens`
- `bugfix/corrigir-responsividade-mobile`
- `docs/guia-instalacao`
- `style/reorganizar-estrutura-html`

---

## Commits Semânticos

### Sintaxe

```
tipo(escopo): descrição
```

### Exemplos

```
feat(header): adicionar logo da empresa
fix(navegacao): corrigir alinhamento do menu
docs(readme): atualizar instrucoes de instalacao
style(css): refatorar variaveis de cores
perf(imagens): otimizar tamanho das imagens
```

### Componentes

**tipo** (obrigatório)
- Define a categoria da mudança
- Ver seção [Tipos de Commits](#tipos-de-commits)

**escopo** (opcional, entre parênteses)
- Indica qual parte do projeto está sendo afetada
- Exemplos: `header`, `footer`, `css`, `imagens`, `readme`, `navbar`, `form`

**descrição** (obrigatório)
- Comece com um verbo no imperativo (adicionar, corrigir, refatorar)
- Máximo 50-60 caracteres
- Explique O QUE foi feito, não COMO
- Use letras minúsculas

---

## Tipos de Commits

### Tipos Padrão

| Tipo | Descrição | Exemplo |
|------|-----------|---------|
| `feat` | Nova funcionalidade | `feat(homepage): criar seção de destaques` |
| `fix` | Correção de bug | `fix(nav): corrigir links quebrados` |
| `docs` | Alterações em documentação | `docs(readme): atualizar instruções` |
| `style` | Formatação de código | `style(css): reformatar indentação` |
| `refactor` | Reorganizar código | `refactor(html): reorganizar estrutura semântica` |
| `perf` | Melhoria de desempenho | `perf(img): comprimir imagens JPG` |
| `test` | Adição de testes | `test(form): validar email obrigatório` |
| `arquivo` | Adição de arquivo | `arquivo(img): Adicionado logo` |

### Tipos Customizados do Projeto

#### arquivo
 Adição ou modificação de mídia (imagens, vídeos, ícones)

**Quando usar:**
- Adicionar novas imagens à pasta `img/`
- Substituir imagens existentes
- Alterar referências de mídia
- Incluir novos assets visuais

**Exemplos:**
```
arquivo(img): adicionar banner de promocao
arquivo(img): substituir foto de perfil da equipe
arquivo(assets): incluir icones de redes sociais
```

**Propósito:** Diferencia mudanças de mídia de CSS ou HTML, facilitando rastreamento de mudanças visuais.

#### chore
**Descrição:** Tarefas de manutenção, configuração e limpeza

**Quando usar:**
- Criar ou atualizar `.gitignore`
- Alterações de configuração do projeto
- Atualizações de dependências
- Limpeza de arquivos temporários
- Reorganização de pastas e estrutura

**Exemplos:**
```
chore(git): adicionar .gitignore para projeto web
chore(estrutura): reorganizar pasta de imagens
chore(limpeza): remover arquivos temporarios
chore(dependencias): atualizar versao do package.json
```

**Propósito:** Separa tarefas administrativas de desenvolvimento real, mantendo histórico mais limpo.

#### ui
**Descrição:** Alterações de interface visual e usabilidade

**Quando usar:**
- Mudanças em layout e espaçamento
- Alterações de cores e tipografia
- Adição de animações CSS que afetam UX
- Redesenho de componentes visuais
- Melhoria de responsividade visual

**Exemplos:**
```
ui(footer): adicionar dark mode ao rodape
ui(header): melhorar espacamento entre elementos
ui(botoes): aumentar tamanho dos botoes para mobile
ui(navegacao): redesenhar menu de navegacao
```

**Propósito:** Diferencia mudanças visuais significativas de simples reformatação de código.

### Tabela Completa

| Tipo | Propósito | Exemplo |
|------|-----------|---------|
| `feat` | Nova funcionalidade | `feat(header): adicionar navegacao sticky` |
| `fix` | Correção de bug | `fix(css): corrigir altura do container` |
| `docs` | Documentação | `docs(readme): adicionar guia de setup` |
| `style` | Formatação de código | `style(html): remover espacos em branco` |
| `refactor` | Reorganizar código | `refactor(css): agrupar media queries` |
| `perf` | Performance | `perf(img): otimizar resolucao de imagens` |
| `test` | Testes | `test(form): validar campos obrigatorios` |
| `arquivo` | Mídia visual | `arquivo(img): adicionar galeria de fotos` |
| `chore` | Manutenção | `chore(git): criar .gitignore` |
| `ui` | Interface visual | `ui(header): redesenhar menu navegacao` |

---

## Regras de Atualização

### Quando Atualizar main

A branch `main` é atualizada quando:
- Feature está completa
- Código testado localmente
- Commits seguem padrões semânticos
- Sem conflitos pendentes

### Fluxo Exemplo

```bash
# 1. Criar branch de feature
git checkout -b feature/homepage

# 2. Desenvolver e fazer commits
git commit -m "feat(header): adicionar logo"
git commit -m "feat(section): criar hero section"

# 3. Voltar para main e atualizar
git checkout main
git pull origin main

# 4. Fazer merge
git merge feature/homepage

# 5. Publicar
git push origin main

# 6. Deletar branches
git branch -d feature/homepage
git push origin --delete feature/homepage
```

---

## Processo de Revisão e Integração

### Pré-Merge Checklist

Antes de fazer merge em `main`, garantir:

- Código está completo e funcional
- Todos os commits seguem convenção semântica
- Sem conflitos com `main`
- `.gitignore` está atualizado
- Não há arquivos desnecessários commitados

### Passo a Passo

```bash
# Passo 1: Atualizar branch local de main
git checkout main
git pull origin main

# Passo 2: Voltar para feature e integrar main
git checkout feature/minha-feature
git merge main

# Passo 3: Resolver conflitos se houver

# Passo 4: Fazer merge da feature em main
git checkout main
git merge feature/minha-feature

# Passo 5: Publicar
git push origin main

# Passo 6: Deletar branch remota
git push origin --delete feature/minha-feature

# Passo 7 (opcional): Deletar branch local
git branch -d feature/minha-feature
```

### Política de Integração

- Usar merge commit para features completas (preserva histórico)
- Usar rebase apenas em branches locais (não em main)
- Evitar squash merge (perde histórico de commits)

---

## Resolução de Conflitos

### O que é um Conflito?

Quando duas branches alteram a mesma linha de código de formas diferentes, Git não sabe qual manter.

### Exemplo de Conflito

**Branch A:**
```html
<h1>Bem-vindo ao Projeto!</h1>
```

**Branch B:**
```html
<h1>Welcome to Project!</h1>
```

**Resultado do Merge (com conflito):**
```html
<<<<<<< HEAD (main)
<h1>Welcome to Project!</h1>
=======
<h1>Bem-vindo ao Projeto!</h1>
>>>>>>> feature/titulo-novo
```

### Como Resolver

**Opção 1: Manter uma versão**
```html
<h1>Bem-vindo ao Projeto!</h1>
```

**Opção 2: Combinar ambas**
```html
<h1>Bem-vindo ao Projeto! / Welcome to Project!</h1>
```

**Opção 3: Usar ferramenta visual**
```bash
git mergetool
```

### Passo a Passo

1. Identificar conflitos:
   ```bash
   git status
   ```

2. Abrir arquivo e resolver manualmente
   - Remover marcadores `<<<<<<<`, `=======`, `>>>>>>>`
   - Manter o código desejado

3. Após resolver:
   ```bash
   git add arquivo-resolvido.html
   git commit -m "fix(merge): resolver conflito no titulo"
   git push origin main
   ```

### Boas Práticas para Evitar Conflitos

- Fazer pull frequentemente: `git pull origin main`
- Branches focadas em uma funcionalidade
- Comunicação clara entre o time (quem está mexendo em quê)
- Evitar alterar muitos arquivos simultaneamente

---

## Boas Práticas

### Commits Atômicos

**Ruim - 1 commit gigante:**
```bash
git commit -m "adicionar tudo"
```

**Bom - Vários commits pequenos:**
```bash
git commit -m "feat(header): adicionar logo"
git commit -m "feat(header): estilizar menu navegacao"
git commit -m "ui(header): melhorar responsividade"
```

### Mensagens Descritivas

**Ruim:**
```bash
git commit -m "fix 1"
git commit -m "mudanca"
git commit -m "ok"
```

**Bom:**
```bash
git commit -m "fix(nav): corrigir alinhamento de itens no mobile"
git commit -m "feat(footer): adicionar links para redes sociais"
git commit -m "chore(git): criar .gitignore para projeto"
```

### Faça Isso

- Sempre usar branches
- Commits pequenos e focados
- Mensagens semânticas
- Pull antes de push
- Comunicar com o time
- Revisar código antes de integrar

### Não Faça Isso

- Commits diretos em `main`
- Mensagens de commit em maiúscula
- Commits com múltiplos tipos de mudança
- Rebase em branches públicas
- Force push sem motivo válido
- Ignorar conflitos

---

## Referências e Documentação

- [Git Documentation](https://git-scm.com/doc)
- [GitHub Flow Guide](https://docs.github.com/en/get-started/using-github/github-flow)
- [Conventional Commits](https://www.conventionalcommits.org/)
- [Semantic Versioning](https://semver.org/)

