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

### Passos

1. **Instalar dependências**
```bash
npm ci
```

2. **Arrancar em dev**
```bash
npm run dev
```

3. **Build de produção**
```bash
npm run build
```

4. **Pré-visualizar build**
```bash
npm run preview
```

5. **Lint (se configurado)**
```bash
npm run lint
```

---

## 🌿 Branching model

- `main` → produção (protegida)
- `develop` → integração (staging)
- `feature/<area>-<descricao>` → nova funcionalidade  
  ex.: `feature/aboutus`, `feature/gallery`
- `fix/<descricao>` → correções/bugs  
  ex.: `fix/contact-button`
- `chore/<descricao>` → manutenção  
  ex.: `chore/update-index-html`
- `docs/<descricao>` → documentação

> Regra: nunca trabalhar diretamente em `main`. Abrir PRs contra `develop`.

---

## 🧠 Commits (Conventional Commits)

Exemplos:
```
feat(aboutus): cria secção inicial com biografia
fix(contact): corrige validação do email no formulário
chore(index): atualiza meta tags og:*
docs(readme): adiciona instruções de execução
style(header): ajusta espaçamentos no menu
refactor(gallery): extrai componente Lightbox
```

---

## 🔀 Pull Requests

1. Cria branch a partir de `develop`.
2. Faz commits pequenos e descritivos.
3. Abre PR como Draft cedo (feature → develop).
4. Mantém a branch atualizada (rebase periódico):
   ```bash
   git fetch origin
   git rebase origin/develop
   git push --force-with-lease
   ```
5. Preenche o template de PR.
6. CI tem de estar verde.
7. 1 aprovação obrigatória (CODEOWNERS).
8. Squash and Merge.

---

## ✅ Definition of Done (DoD)

- Build e lint verdes no CI
- Acessibilidade mínima (alt/aria, foco visível)
- Responsividade (mobile e desktop)
- Sem regressões nas outras secções
- README/docs atualizados se necessário

---

## 🤝 Convenções de código (resumo)

- Componentes em PascalCase (AboutUs.jsx)
- Um componente por ficheiro
- Evitar lógica pesada no JSX (extrair para helpers/hooks)
- Imagens com alt e elementos interativos com aria-*
- Não misturar feature com chore na mesma PR

---

## 🧪 Testes (se/quando existirem)

- Colocar testes em `src/__tests__/` ou `*.test.jsx`
- Executar no CI com `npm test`

---

## 🔧 CI (GitHub Actions)

O workflow vive em `.github/workflows/ci.yml` e executa:
```
npm ci
npm run lint --if-present
npm test --if-present
npm run build
```

Em **Settings → Branches → main**, ativa “Require status checks to pass” e seleciona o check do CI.

---

## 👥 Revisões automáticas (CODEOWNERS)

```
* @leocoelho1982 @ruidiniz02
/src/sections/aboutus/** @leocoelho1982
/src/sections/contact/** @ruidiniz02
/src/sections/gallery/** @ruidiniz02
/src/components/** @leocoelho1982 @ruidiniz02
```

---

## 📦 Releases

```bash
git checkout main
git pull
git merge --ff-only develop
git tag -a v0.1.0 -m "Primeira release (layout+about+contact+gallery)"
git push origin main --tags
```

---

## 🆘 Hotfix rápido

```bash
git checkout main && git pull
git checkout -b fix/<descricao>
# corrigir, commit, push...
# abrir PR para main (após merge, back-merge para develop)
```
