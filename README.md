# Rebello – Site (React + Vite)

Projeto de treino de workflow em equipa no GitHub com 5 secções:
**Header**, **About Us**, **Contact**, **Gallery** e **Footer**.

> Objetivo: simular um fluxo “empresa grande” com branches protegidas, CI, revisões de código e releases.

---

## 🚀 Stack
- **React 18+** com **Vite**
- **ESLint** (regras base)
- **GitHub Actions** (CI: build, lint e testes se existirem)

---

## 🧩 Estrutura (sugerida)
src/
components/
Header.jsx
Footer.jsx
sections/
AboutUs.jsx
Contact.jsx
Gallery.jsx
assets/
App.jsx
main.jsx
index.html


---

## ▶️ Como correr localmente

```bash
# 1) instalar dependências
npm ci

# 2) arrancar em dev
npm run dev

# 3) build de produção
npm run build

# 4) pré-visualizar build
npm run preview

# 5) lint (se configurado)
npm run lint

## 🌿 Branching model

# main → produção (protegida)

develop → integração (staging)

feature/<area>-<descricao> → nova funcionalidade
e.g. feature/aboutus, feature/gallery

fix/<descricao> → correções/bugs
e.g. fix/contact-button

chore/<descricao> → tarefas de manutenção
e.g. chore/update-index-html

docs/<descricao> → documentação

Regra: nunca trabalhar diretamente em main. Abrir PRs contra develop.

## 🧠 Commits (Conventional Commits)

feat(aboutus): cria secção inicial com biografia
fix(contact): corrige validação do email no formulário
chore(index): atualiza meta tags og:*
docs(readme): adiciona instruções de execução
style(header): ajusta espaçamentos no menu
refactor(gallery): extrai componente Lightbox

🔀 Pull Requests

1. Cria branch a partir de develop.

2. Faz commits pequenos e descritivos.

3. Abre PR como Draft cedo (feature → develop).

4. Mantém a branch atualizada (rebase periódico):
git fetch origin
git rebase origin/develop
git push --force-with-lease

5. Preenche o template de PR.

6. CI tem de estar verde.

7. aprovação obrigatória (CODEOWNERS).

8. Squash and Merge.

✅ Definition of Done (DoD)

Build e lint verdes no CI

Acessibilidade mínima (alt/aria, foco visível)

Responsividade (mobile e desktop)

Sem regressões nas outras secções

README/docs atualizados se necessário

🤝 Convenções de código (resumo)

Componentes em PascalCase (AboutUs.jsx)

Um componente por ficheiro

Evitar lógica pesada no JSX (extrair para helpers/hooks)

Imagens com alt e elementos interactivos com aria-*

Não misturar feature com chore na mesma PR

🧪 Testes (se/quando existirem)

Colocar testes em src/__tests__/ ou *.test.jsx

Executar no CI com npm test

🔧 CI (GitHub Actions)

O workflow vive em .github/workflows/ci.yml e executa:

npm ci

npm run lint --if-present

npm test --if-present

npm run build

Em Settings → Branches → main, “Require status checks to pass” deve incluir o check do CI.

👥 Revisões automáticas

CODEOWNERS (em .github/CODEOWNERS) atribui revisores automaticamente:
* @dev1 @dev2
/src/sections/aboutus/** @dev1
/src/sections/contact/** @dev2
/src/sections/gallery/** @dev2
/src/components/** @dev1 @dev2

📦 Releases

Quando develop estiver estável:
git checkout main
git pull
git merge --ff-only develop
git tag -a v0.1.0 -m "Primeira release (layout+about+contact+gallery)"
git push origin main --tags

🆘 Hotfix rápido

Bug em produção?
git checkout main && git pull
git checkout -b fix/<descricao>
# corrigir, commit, push...
# abrir PR para main (após merge, back-merge para develop)



