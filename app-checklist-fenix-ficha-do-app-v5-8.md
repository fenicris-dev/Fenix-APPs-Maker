# APP CHECKLIST FÊNIX — FICHA DO APP (v5.8)

> **Complemento** do Livro das Regras, do Guia da Biblioteca e do Bloco de Entrega. Não os substitui: eles continuam sendo as fontes oficiais (regra 73). Este documento só seleciona os blocos aplicáveis a cada app, para economizar tokens e tempo.

## Como usar (fluxo rápido)

1. **Anexar na 1ª mensagem do app:** este documento preenchido + o pacote da biblioteca (.zip). Nunca trabalhar de memória.
2. **Preencher as seções 1 a 3** e confirmar com o Cristiano antes de construir (regra 52).
3. **Construir usando só os blocos marcados** (seção 4). Bloco não marcado é pulado.
4. **Registrar as informações cruciais** no Changelog do app (seção 5).
5. **Encerrar toda entrega com a Conferência** (seção 6) — linha obrigatória.

---

## 1. Identificação do app

- Identificador (`FenixCore.init`): `fenix-______________`
- Nome de exibição: ______________
- Versão atual: `vX.X`
- Tipo de trabalho: ( ) App novo | ( ) Alteração | ( ) Trazer app antigo ao padrão
- Selo atual no `<head>`: Livro `vX.X` | Ficha `____`
- URL publicada (GitHub Pages): ______________
- Repositório: ______________

## 2. Grupos da Ficha (A–J)

Marcar com **X**. Grupos não marcados são pulados (regra 52).

- [ ] **A — Banco Firestore ativo** (regras 1, 46, 66)
- [ ] **B — Login por e-mail/senha** (regras 23–27, 67)
- [ ] **G — Dashboard clicável** (regra 54)
- [ ] **H — Login com Google** (regras 56, 58)
- [ ] **I — Sincronia entre aparelhos** (regra 57)
- [ ] **J — Tema escuro opcional** (regra 60)
- [ ] Grupos **C, D, E, F**: preencher junto, conforme a Ficha completa no Livro.

**Outros dados:**
- Outras APIs (além de Firebase, ViaCEP e BrasilAPI): ______________
- Observações de layout: ______________
- PWA: ( ) sim | ( ) não
- Multiempresa (`criarModuloEmpresas` etc.): ( ) sim | ( ) não

## 3. Funcionalidade principal (3–5 itens)

1. ______________
2. ______________
3. ______________
4. ______________
5. ______________

---

## 4. Seleção de blocos

### 4.1 Obrigatórios em TODO app (independem de grupo)

- Arquitetura: core centralizado (1), carregador oficial (2), offline (3), indicador de conexão (4)
- Identidade visual: paleta, degradê, águia, layout, mobile, toque 44px, mensagens, rodapé (14–22)
- Splash com holofotes (32) e toque Asas + animações (59)
- Preferências: som e reduzir animações (60)
- Versionamento, Changelog, Manual e Sobre (7–13)
- Máscaras automáticas, validação de CPF/CNPJ, datas e moeda (38–40)
- Segurança: texto seguro (64), esquema dos dados (65), acessibilidade (69), saída protegida (71)
- Backup/importação (44), Compartilhar (74), onde guardar os dados (77)
- Selos: Livro (53) e versões `v | c` (61); teste de 15 dias e somente leitura (62–63)
- Estrutura de pastas (78), teste de fumaça (68), plano de volta (70)
- Bloco de Entrega completo + Conferência (72)

### 4.2 Só se **A** (banco)

- Banco desligado por padrão (1), cota/paginação (66), regras do Firestore (46)

### 4.3 Só se **B** (login)

- Template de login (23–26), Termos/Privacidade (27), onboarding (28–29)
- Nome/avatar no topo (30–31), exportar dados e excluir conta (67)

### 4.4 Só se **H** (Google)

- Botão Google + licença definitiva (58), `entrarComGoogle`/`resultadoRedirecionamento` (56)

### 4.5 Só se **I** (sincronia)

- `criarSincronia` (app novo) ou `criarModuloSincronia` (legado) (57); tempo real + fila offline

### 4.6 Só se **J** (tema escuro)

- Seletor Tema + variáveis CSS (60)

### 4.7 Só se **G** (dashboard)

- Dashboard clicável com `FenixCore.dashboard.montar` (54)

### 4.8 Só se o app usa **CPF/CNPJ/CEP**

- Cadastros PF/PJ (33–36), aviso de uso do documento (37), fluxo do CNPJ (35), CEP (33)

### 4.9 Só se o app emite **PDF/recibos/orçamentos**

- Cabeçalho padrão com logo Azul + dados do perfil (45)

### 4.10 Só se for **trazer app antigo ao padrão**

- Roteiro da regra 55: inventário, proteção de dados, etapas; não mexer no não solicitado (55f)

---

## 5. Registro crucial do app (Changelog mínimo)

Copiar e manter atualizado no Changelog (regra 12):

- Selo Livro: `vX.X` | Ficha: `____`
- Core mínimo aceito: `c X.X`
- Chaves do localStorage / coleções ativas: ______________
- Versão do esquema dos dados: `__`
- Login Google: sim/não | Sincronia: sim/não | Tema escuro: sim/não
- API externa extra: ______________
- Versão de volta: `vX.X`

---

## 6. Conferência de entrega (copiar no fim de TODA entrega)

> Conferência de entrega: versão no nome: sim/não | index.html: sim/não | zip com LEIAME: sim/não/não se aplica | selo: sim/não | Changelog e Manual: sim/não | teste de fumaça: sim/não | versão de volta: vX.X | botão Compartilhar: sim/não | onde guardar os dados: sim/não | estrutura de pastas: sim/não

> **Fontes oficiais:** Livro das Regras, Guia da Biblioteca e Bloco de Entrega (pacote anexado). Se os links do GitHub Pages não abrirem, usar `https://raw.githubusercontent.com/fenicris-dev/Fenix-Core/main/` + caminho; se nem esse abrir, pedir os arquivos (regra 73).