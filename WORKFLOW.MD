Workflow de Desenvolvimento
1. Modelo de Workflow
GitHub Flow
Uma única branch principal (main), sempre pronta para produção.

Todas as branches de trabalho são criadas a partir de main e, após concluídas e revisadas, retornam para main por meio de merge.

main
 ├── feature/*
 ├── bugfix/*
 ├── docs/*
 ├── style/*
 └── hotfix/*
        ↓
       main

2. Estratégia de Branches
Tipos de Branches
feature/ → novas funcionalidades
bugfix/ → correções de bugs
docs/ → alterações na documentação
style/ → alterações de formatação e estilo do código
hotfix/ → correções urgentes em produção
Exemplos
feature/login
feature/user-profile
bugfix/login-validation
docs/update-readme
style/header-layout
hotfix/payment-error

Fluxo
main
  ↓
feature/ | bugfix/ | docs/ | style/ | hotfix/
  ↓
main

Regras
Todas as branches devem nascer de main.
Todos os merges devem retornar para main.
Nunca fazer merge de uma branch de trabalho em outra branch de trabalho.
Deletar a branch após o merge ser concluído.
Não fazer push diretamente em main.
3. Commits Semânticos
Sintaxe
tipo(escopo): descrição

Exemplo
feat(header): adiciona logo da empresa

Escopo
O escopo é opcional e deve indicar a área afetada pelo commit.

Exemplos:

header
footer
css
images
readme
navbar
form

Regras da descrição
Utilizar verbo no presente.
Manter a descrição curta, preferencialmente entre 50 e 60 caracteres.
Explicar o que foi feito.
Utilizar letras minúsculas.
Não utilizar ponto final.
4. Tipos de Commits
Tipo	Descrição
feat	Nova funcionalidade
fix	Correção de bug
docs	Alteração na documentação
style	Formatação do código sem alteração de comportamento
refactor	Reorganização do código sem alteração de comportamento
perf	Melhoria de desempenho
test	Adição ou alteração de testes
media	Adição ou modificação de imagens, vídeos ou ícones
chore	Tarefas de manutenção, configuração e limpeza
ui	Alteração da interface visual
ux	Alteração relacionada à usabilidade
context	Adição ou alteração de arquivos de contexto para IA

Exemplos
feat(login): adiciona autenticação
fix(form): corrige validação de email
docs(readme): atualiza instruções de instalação
style(css): organiza propriedades do header
refactor(navbar): simplifica estrutura do menu
perf(images): otimiza carregamento das imagens
test(login): adiciona testes de autenticação
media(images): adiciona ícones do dashboard
chore(deps): atualiza dependências
ui(header): ajusta layout do cabeçalho
ux(form): melhora mensagens de validação
context(ai): atualiza contexto do projeto

feat, fix, docs, style, refactor, perf, test e chore seguem a ideia do Conventional Commits. media, ui, ux e context são tipos personalizados para o projeto.

5. Regras de Atualização
A main deve ser atualizada somente quando:

A funcionalidade estiver completa.
O código tiver sido testado localmente.
Os commits seguirem a convenção definida.
Não existirem conflitos pendentes.
A branch estiver atualizada com a main.
Regra principal
NÃO fazer push diretamente em main.

Conflitos devem ser resolvidos na branch de trabalho antes da integração.

Frequência
Features pequenas: integração conforme concluídas, preferencialmente diariamente.
Bugs urgentes: integração imediatamente após correção e validação.
Documentação: conforme necessário.
6. Processo de Revisão e Integração
Pre-Merge Checklist
 Código está completo e funcional.
 Código foi testado localmente.
 Todos os commits seguem a convenção semântica.
 Branch está atualizada com main.
 Não existem conflitos.
 .gitignore está atualizado.
 Não existem arquivos desnecessários commitados.
Fluxo de Integração
git checkout main
git pull origin main

git checkout feature/minha-feature
git merge main

# Resolver conflitos, se houver
# Testar novamente

git checkout main
git merge feature/minha-feature

git push origin main

git push origin --delete feature/minha-feature
git branch -d feature/minha-feature

7. Política de Merge
Utilizar merge commit para features completas.
Utilizar rebase apenas em branches locais.
Evitar squash merge.
Não reescrever o histórico da main.
Resolver conflitos antes do merge.
Fluxo resumido
1. Atualizar main
       ↓
2. Criar branch
       ↓
3. Desenvolver
       ↓
4. Fazer commits semânticos
       ↓
5. Atualizar branch com main
       ↓
6. Testar
       ↓
7. Merge para main
       ↓
8. Push
       ↓
9. Deletar branch