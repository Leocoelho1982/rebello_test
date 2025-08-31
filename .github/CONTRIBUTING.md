# Contributing Guide

## 🔀 Branches
- `main` → Produção (protegida)
- `develop` → Integração (todas as features juntam aqui)
- `feature/<area>-<descricao>` → Desenvolvimento de novas funcionalidades
- `fix/<descricao>` → Correções rápidas (bugs)

## 📝 Commits (padrão Conventional Commits)
- `feat:` → nova funcionalidade
- `fix:` → correção de bug
- `docs:` → alterações em documentação
- `style:` → apenas estilos (CSS, formatação)
- `refactor:` → refatoração sem alterar funcionalidade
- `test:` → adicionar ou atualizar testes
- `chore:` → tarefas de manutenção (configs, CI, dependências)

Exemplo:
feat(aboutus): cria componente inicial da secção About Us
fix(contact): corrige validação do formulário de email


## 🔎 Pull Requests
- Criar PR sempre contra `develop`
- Preencher o template (`.github/PULL_REQUEST_TEMPLATE.md`)
- CI deve estar verde
- Requer **1 aprovação obrigatória**
- Usar **Squash and Merge**

## ✅ Definition of Done
- Código compila e CI está verde
- Revisão feita e aprovada
- Documentação/README atualizados (se necessário)
- Acessibilidade mínima (alt, aria, contraste)
