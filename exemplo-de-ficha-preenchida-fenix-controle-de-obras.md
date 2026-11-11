# FICHA DO APP — EXEMPLO PREENCHIDO

> **Ilustrativo.** Mostra como a ficha chega preenchida na 1ª mensagem de um app. Dados fictícios.

## 1. Identificação do app

- Identificador (`FenixCore.init`): `fenix-controle-obras`
- Nome de exibição: Controle de Obras
- Versão atual: `v1.0`
- Tipo de trabalho: **( X ) App novo** | ( ) Alteração | ( ) Trazer app antigo ao padrão
- Selo atual no `<head>`: Livro `v5.8` | Ficha `A,B,G,H,I,J`
- URL publicada (GitHub Pages): `https://fenicris-dev.github.io/Fenix-Controle-de-Obras/`
- Repositório: mesma URL, repositório `Fenix-Controle-de-Obras`

## 2. Grupos da Ficha (A–J)

Marcar com **X**. Grupos não marcados são pulados (regra 52).

- [X] **A — Banco Firestore ativo** (regras 1, 46, 66)
- [X] **B — Login por e-mail/senha** (regras 23–27, 67)
- [ ] **G — Dashboard clicável** (regra 54) — **marcado no exemplo, ver abaixo**
- [X] **H — Login com Google** (regras 56, 58)
- [X] **I — Sincronia entre aparelhos** (regra 57)
- [X] **J — Tema escuro opcional** (regra 60)
- Grupos **C, D, E, F**: não se aplicam neste app.

**Outros dados:**
- Outras APIs (além de Firebase, ViaCEP e BrasilAPI): nenhuma
- Observações de layout: menu lateral, barra de abas embaixo no celular
- PWA: **( X ) sim** | ( ) não
- Multiempresa: ( ) sim | **( X ) não**

## 3. Funcionalidade principal (3–5 itens)

1. Cadastrar obras (com CNPJ do cliente e consulta na Receita)
2. Acompanhar etapas de cada obra
3. Emitir relatório em PDF com cabeçalho padrão
4. Dashboard com obras em andamento, interrompidas e concluídas

---

## 4. Seleção de blocos

- **4.1 Obrigatórios:** todos (arquitetura, identidade, splash, preferências, versionamento, máscaras, segurança, backup, compartilhar, armazenamento, selos, estrutura, teste de fumaça, plano de volta, conferência).
- **4.2 (A):** banco desligado por padrão, cota/paginação, regras do Firestore.
- **4.3 (B):** template de login, Termos/Privacidade, onboarding, nome/avatar, exportar dados e excluir conta.
- **4.4 (H):** botão Google + licença definitiva, `entrarComGoogle`/`resultadoRedirecionamento`.
- **4.5 (I):** `criarSincronia` (app novo), tempo real + fila offline.
- **4.6 (J):** seletor Tema + variáveis CSS.
- **4.7 (G):** dashboard clicável com `FenixCore.dashboard.montar`.
- **4.8 (CPF/CNPJ/CEP):** fluxo do CNPJ, cadastros PF/PJ, aviso de uso do documento, CEP.
- **4.9 (PDF):** cabeçalho padrão com logo Azul + dados do perfil.

---

## 5. Registro crucial do app (Changelog mínimo)

- Selo Livro: `v5.8` | Ficha: `A,B,G,H,I,J`
- Core mínimo aceito: `c 5.8`
- Chaves do localStorage / coleções ativas: `fenix_controle_obras_obras`, `fenix_controle_obras_etapas`
- Versão do esquema dos dados: `1`
- Login Google: **sim** | Sincronia: **sim** | Tema escuro: **sim**
- API externa extra: Brasília (Receita) + ViaCEP
- Versão de volta: `v1.0`

---

## 6. Conferência de entrega (copiar no fim de TODA entrega)

> Conferência de entrega: versão no nome: sim | index.html: sim | zip com LEIAME: sim | selo: sim | Changelog e Manual: sim | teste de fumaça: sim | versão de volta: v1.0 | botão Compartilhar: sim | onde guardar os dados: sim | estrutura de pastas: sim

> **Fontes oficiais:** Livro das Regras, Guia da Biblioteca e Bloco de Entrega (pacote anexado). Se os links do GitHub Pages não abrirem, usar `https://raw.githubusercontent.com/fenicris-dev/Fenix-Core/main/` + caminho; se nem esse abrir, pedir os arquivos (regra 73).