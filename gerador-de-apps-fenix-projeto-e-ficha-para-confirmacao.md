# GERADOR DE APPS FÊNIX — PROJETO E FICHA

> **Etapa de desenho.** Nada foi codado ainda: esta é a proposta para você confirmar antes de eu construir.

---

## 1. O que é

App Fênix **real**, de uso interno (nosso, não de cliente), publicado no GitHub Pages. Ele:

1. Cadastra e mantém os **cartões dos apps** (as informações cruciais de cada app Fênix).
2. Lê o **`acervo.json`** e o **`versao.json`** no GitHub para saber a versão atual do Livro/Core e o que existe no acervo.
3. Gera, com um clique, a **ficha preenchida** (padrão CHECKLIST v5.8) e o **prompt completo de abertura** para colar no chat comigo.
4. Guarda os cartões na **nuvem Fênix**, para você acessar de qualquer aparelho.

**Princípio da versão viva:** o gerador nunca copia o Livro nem o Core para dentro de si. Ele **consulta o GitHub** na hora de usar; se amanhã o Livro subir para v5.9, o gerador já lê e aplica a 5.9, sem republicar.

---

## 2. Ficha do gerador (proposta — CONFIRMAR)

> Grupos marcados com **X**; os não marcados são pulados (regra 52).

**Seção 1 — Identificação**

- Identificador (`FenixCore.init`): `fenix-gerador-de-apps`
- Nome de exibição: **Gerador de Apps Fênix**
- Versão: `v1.0`
- Tipo de trabalho: **( X ) App novo** | ( ) Alteração | ( ) Trazer ao padrão
- Selo a aplicar no `<head>`: Livro **v5.8** | Ficha **A,B,I** (H e J opcionais)
- Repositório sugerido: `Fenix-Gerador-de-Apps`

**Seção 2 — Grupos da Ficha (A–J)**

- [X] **A — Banco Firestore ativo** (guardar os cartões na nuvem)
- [X] **B — Login por e-mail/senha** (só você acessa)
- [ ] **C, D, E, F** — não se aplicam
- [ ] **G — Dashboard clicável** — não precisa num app interno simples
- [ ] **H — Login com Google** — sugiro deixar para depois (precisa de licença definitiva; você usa e-mail/senha por ora)
- [X] **I — Sincronia entre aparelhos** (cartões acessíveis em qualquer aparelho)
- [X] **J — Tema escuro opcional** — conforto de uso

**Outros dados**

- Outras APIs (além de Firebase, ViaCEP e BrasilAPI): **somente fetch ao GitHub** (acervo.json, versao.json)
- Observações de layout: menu lateral, barra de abas embaixo no celular
- PWA: **( X ) sim** | ( ) não
- Multiempresa: ( ) sim | **( X ) não** — os dados são pessoais (`dados_pessoais`)

**Seção 3 — Funcionalidade principal (5 itens)**

1. Cadastrar e manter cartões dos apps Fênix (dados cruciais de cada um)
2. Ler `acervo.json` e `versao.json` do GitHub e mostrar a versão atual do Livro/Core
3. Gerar a ficha preenchida (markdown) no padrão CHECKLIST v5.8
4. Gerar o prompt completo de abertura para colar no chat comigo
5. Sincronizar os cartões na nuvem entre aparelhos

---

## 3. Dados guardados na nuvem (cartão de cada app)

Caminho: `dados_pessoais/{uid}/fenix-gerador-de-apps/cartoes/{id}`

Cada cartão guarda:

- `id` — identificador do app (`fenix-nome-do-app`)
- `nomeApp` — nome de exibição
- `tipo` — `novo` | `alteracao` | `padrao`
- `versao` — versão atual do app
- `seloLivro` / `seloFicha` — selos no `<head>` daquele app
- `grupos` — letras A–J marcadas
- `funcionalidades` — lista de 3–5 itens
- `apisExtras`, `pwa`, `multiempresa`, `obsLayout`
- `coreMinimo`, `chavesLocal`, `versaoEsquema`
- `loginGoogle`, `sincronia`, `temaEscuro`
- `versaoDeVolta`, `criadoEm`, `atualizadoEm`

---

## 4. Telas e fluxo

| # | Tela | O que faz |
|---|------|-----------|
| 1 | **Splash** | Template oficial, some ao carregar (regra 32) |
| 2 | **Login** | Template oficial, só e-mail/senha (regra 23) |
| 3 | **Onboarding** | Primeiro acesso: nome e e-mail (regra 28) |
| 4 | **Home — Meus apps** | Lista de cartões + botão "Novo app" + ações por cartão (Gerar prompt, Editar, Excluir) |
| 5 | **Formulário do app** | Campos abaixo; edita ou cria cartão |
| 6 | **Resultado** | Ficha gerada + prompt pronto, com botões Copiar |
| 7 | **Ajuda/Sobre** | Manual, Changelog, preferências, onde guardar dados, exportar, excluir conta, compartilhar |

---

## 5. Campos do formulário (tela 5)

- Nome do app (vira identificador e nome de exibição)
- Tipo de trabalho (app novo / alteração / trazer ao padrão)
- Versão atual (se for alteração)
- Selo atual no `<head>` (Livro e Ficha), se o app já existir
- Grupos A–J (checkboxes) — com avisos automáticos:
  - **I** sem **A** e **B** → "Sincronia exige banco e login"
  - **H** → "Google vem junto com login"
- Funcionalidade principal (3–5 itens)
- APIs extras | PWA sim/não | Multiempresa sim/não
- Observações de layout
- **O que esta entrega faz** (obrigatório em atualizações)

---

## 6. Como o "Gerar prompt" trabalha

1. Lê o cartão preenchido.
2. Lê `acervo.json` + `versao.json` no GitHub (com cache de 6h e fallback para `raw.githubusercontent.com`).
3. Compara o `seloLivro` do cartão com a versão atual do acervo: se houver livro mais novo, avisa "este app está na v5.7 e o Livro já está na v5.8".
4. Monta a ficha (seções 1–5 do CHECKLIST) já preenchida.
5. Monta o prompt de abertura, incluindo a lista de assets pertinentes (ícones, logos, templates) conforme os grupos marcados.
6. Devolve os dois blocos com botão **Copiar**.

---

## 7. Blocos do core que o gerador vai usar

- **Obrigatórios:** carregador oficial, splash, identidade Fênix, selos, preferências, backup, compartilhar, armazenamento, segurança, saída protegida, versionamento, Changelog e Manual.
- **A (banco):** `initFirebaseComCache` + `init`, cota/paginação, regras do Firestore.
- **B (login):** `criarModuloAuth`, template de login, onboarding, Termos/Privacidade, excluir conta.
- **I (sincronia):** `criarSincronia` com `escopo: "pessoal"` para os cartões.
- **J (tema):** `preferencias.montarTela` + variáveis CSS.

---

## 8. O que preciso que você confirme

1. **Ficha aprovada?** (grupos **A, B, I, J** — Google fica para depois)
2. **Nome do repositório:** `Fenix-Gerador-de-Apps` serve?
3. **Acesso só seu** (e-mail/senha) está OK por enquanto?
4. **PWA: sim** está OK?

Confirmando esses quatro pontos, eu parto para a construção (v1.0), seguindo o Bloco de Entrega. Se preferir mudar algo na ficha, me diga o que ajustar.