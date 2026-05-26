# 📋 Guia: Como Adicionar uma Nova Empresa Representada

> **Arquivo:** `index2.html`  
> **Padrão de URL:** `/representante-NOMEDAEMPRESA/`  
> **Imagem do logo:** `/imagens-home/NOMEDAEMPRESA-logo.webp`

---

## 🔧 Antes de Começar — Preencha os Dados

Substitua esses valores nos códigos abaixo:

| Placeholder | O que colocar | Exemplo |
|---|---|---|
| `NOMEDAEMPRESA` | Nome em minúsculas sem espaço (para URLs e classes CSS) | `tramontina` |
| `NOMEDISPLAY` | Nome bonito da empresa (para exibir na tela) | `Tramontina` |
| `NOMEDISPLAY_UPPER` | Nome em MAIÚSCULAS (para o footer) | `TRAMONTINA` |
| `#CORDA_EMPRESA` | Cor hexadecimal da marca | `#E4002B` |
| `DESCRICAO_CURTA` | Descrição curta da linha de produtos | `Linha de Utensílios Domésticos e Profissionais` |
| `IMAGEM_LOGO` | Caminho da imagem .webp do logo | `/imagens-home/tramontina-logo.webp` |

---

## ✅ PASSO 1 — Adicionar a Imagem do Logo

Salve o logo da empresa no formato `.webp` na pasta:

```
/imagens-home/NOMEDAEMPRESA-logo.webp
```

**Exemplo:** `/imagens-home/tramontina-logo.webp`

> ⚠️ **Recomendação:** imagem quadrada, mínimo 160x160px, fundo transparente.

---

## ✅ PASSO 2 — CSS: Variáveis de Cor (3 locais)

### 2A — Variáveis CSS `:root` (± linha 1165)

Procure por `--brand-regina: #fad112;` e **adicione logo abaixo:**

```css
--brand-NOMEDAEMPRESA: #CORDA_EMPRESA;
```

**Exemplo:**
```css
--brand-regina: #fad112;
--brand-tramontina: #E4002B;   /* ← NOVA EMPRESA */
```

---

### 2B — Classes `.text-brand-` no fallback CSS (2 locais!)

**Primeiro local (± linha 656):** Procure por `.text-brand-regina` e adicione abaixo:

```css
.text-brand-NOMEDAEMPRESA {
    color: #CORDA_EMPRESA
}
```

**Segundo local (± linha 1191):** Procure por `.text-brand-regina` (com `!important`) e adicione abaixo:

```css
.text-brand-NOMEDAEMPRESA {
    color: var(--brand-NOMEDAEMPRESA) !important;
}
```

---

### 2C — Classe `.hover-brand-` para o Header (± linha 2026)

Procure por `.hover-brand-regina:hover` e adicione abaixo:

```css
.hover-brand-NOMEDAEMPRESA:hover {
    color: #CORDA_EMPRESA !important;
}
```

**Exemplo completo:**
```css
.hover-brand-regina:hover {
    color: #fad112 !important;
}

.hover-brand-tramontina:hover {
    color: #E4002B !important;
}
```

---

## ✅ PASSO 3 — Header Desktop (± linha 2067)

Procure pelo link da Cerâmica Regina no menu desktop:

```html
<a href="/representante-ceramica-regina/"
    class="text-[12px] lg:text-[13px] font-bold uppercase tracking-widest text-brand-navy/70 header-nav-link hover-brand-regina">Cerâmica
    Regina</a>
```

**Adicione ANTES do link "Contato"** (que fica logo depois):

```html
<a href="/representante-NOMEDAEMPRESA/"
    class="text-[12px] lg:text-[13px] font-bold uppercase tracking-widest text-brand-navy/70 header-nav-link hover-brand-NOMEDAEMPRESA">NOMEDISPLAY</a>
```

**Exemplo:**
```html
<a href="/representante-tramontina/"
    class="text-[12px] lg:text-[13px] font-bold uppercase tracking-widest text-brand-navy/70 header-nav-link hover-brand-tramontina">Tramontina</a>
```

---

## ✅ PASSO 4 — Header Mobile (± linha 2111)

Procure pelo link da Cerâmica Regina no menu mobile:

```html
<a href="/representante-ceramica-regina/"
    class="text-lg font-display font-medium text-brand-navy header-nav-link hover-brand-regina">Cerâmica
    Regina</a>
```

**Adicione ANTES do link "Contato"** mobile:

```html
<a href="/representante-NOMEDAEMPRESA/"
    class="text-lg font-display font-medium text-brand-navy header-nav-link hover-brand-NOMEDAEMPRESA">NOMEDISPLAY</a>
```

**Exemplo:**
```html
<a href="/representante-tramontina/"
    class="text-lg font-display font-medium text-brand-navy header-nav-link hover-brand-tramontina">Tramontina</a>
```

---

## ✅ PASSO 5 — Card de Portfólio / Seção 4 (± linha 2475)

Procure o fechamento do card da Cerâmica Regina (`</div>` do card) e adicione o novo card **ANTES do fechamento do grid** (`</div>` da `grid grid-cols-1`).

Copie e cole o bloco abaixo, substituindo os placeholders:

```html
<!-- NOMEDISPLAY -->
<div class="group cursor-pointer bg-white rounded-[32px] p-8 shadow-sm hover:shadow-2xl transition-all duration-500 border border-brand-neutral/10 flex flex-col h-full js-scroll-anim"
    style="opacity:0; transform:translateY(20px); transition-delay: 0.4s;">
    <div class="h-44 mb-6 flex items-center justify-center p-2">
        <img src="IMAGEM_LOGO" alt="NOMEDISPLAY Logo"
            class="max-h-full max-w-full object-contain group-hover:scale-105 transition-transform duration-500"
            loading="lazy" decoding="async" width="160" height="160" />
    </div>
    <div class="mt-auto">
        <h4
            class="text-xl font-display font-black text-brand-NOMEDAEMPRESA group-hover:text-brand-accent transition-colors mb-2">
            NOMEDISPLAY</h4>
        <p class="text-sm text-brand-navy/60 mb-6">DESCRICAO_CURTA</p>
        <a href="/representante-NOMEDAEMPRESA/"
            class="inline-flex items-center gap-2 text-sm font-bold text-brand-NOMEDAEMPRESA hover:text-brand-navy transition-colors">
            Conhecer <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16"
                viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"
                stroke-linecap="round" stroke-linejoin="round"
                class="lucide lucide-arrow-right group-hover:translate-x-1 transition-transform">
                <path d="M5 12h14" />
                <path d="m12 5 7 7-7 7" />
            </svg>
        </a>
    </div>
</div>
```

> **Nota sobre `transition-delay`:** as empresas atuais usam `0s`, `0.1s`, `0.2s`, `0.3s`. Para a 5ª empresa use `0.4s`, para a 6ª use `0.5s`, etc.

> **Nota sobre o grid:** O grid atual é `lg:grid-cols-4`. Se adicionar uma 5ª empresa, considere mudar para `lg:grid-cols-5` ou manter 4 colunas (a 5ª ficará na linha debaixo, centralizada).

---

## ✅ PASSO 6 — Footer: Marcas Representadas (± linha 4334)

Procure pelo último item da lista no footer (Cerâmica Regina):

```html
<a href="/representante-ceramica-regina/" class="brand-item">
    <div class="brand-dot"></div>
    <span class="brand-item-name">CERÂMICA REGINA</span>
</a>
```

**Adicione logo abaixo:**

```html
<a href="/representante-NOMEDAEMPRESA/" class="brand-item">
    <div class="brand-dot"></div>
    <span class="brand-item-name">NOMEDISPLAY_UPPER</span>
</a>
```

**Exemplo:**
```html
<a href="/representante-tramontina/" class="brand-item">
    <div class="brand-dot"></div>
    <span class="brand-item-name">TRAMONTINA</span>
</a>
```

---

## ✅ PASSO 7 — Texto SEO / Seção 12 (± linha 4264)

Atualize o texto SEO adicionando o nome da nova empresa.

**Antes:**
```html
<h2 class="font-bold text-brand-navy/60 mb-2">Representante Comercial em São Paulo — Weck, Tecnocuba,
    Multiflon
    e Cerâmica Regina</h2>
```

**Depois:**
```html
<h2 class="font-bold text-brand-navy/60 mb-2">Representante Comercial em São Paulo — Weck, Tecnocuba,
    Multiflon, Cerâmica Regina
    e NOMEDISPLAY</h2>
```

---

## ✅ PASSO 8 — Meta Description (linha 18)

Procure a tag `<meta name="description">` no `<head>` (linha 18):

```html
<meta name="description"
    content="Silvio Macedo — representante comercial B2B em São Paulo há mais de 35 anos. Portfólio: Weck, Tecnocuba, Multiflon e Cerâmica Regina. Atendimento em todo o Estado de SP.">
```

**Atualize adicionando o nome da nova empresa:**

```html
<meta name="description"
    content="Silvio Macedo — representante comercial B2B em São Paulo há mais de 35 anos. Portfólio: Weck, Tecnocuba, Multiflon, Cerâmica Regina e NOMEDISPLAY. Atendimento em todo o Estado de SP.">
```

**Exemplo:**
```html
<meta name="description"
    content="Silvio Macedo — representante comercial B2B em São Paulo há mais de 35 anos. Portfólio: Weck, Tecnocuba, Multiflon, Cerâmica Regina e Tramontina. Atendimento em todo o Estado de SP.">
```

---

## 📌 Resumo — Checklist Rápido

Use este checklist para garantir que não esqueceu nenhum ponto:

- [ ] **Imagem:** salvou `/imagens-home/NOMEDAEMPRESA-logo.webp`
- [ ] **CSS `:root`** (± linha 1165): adicionou `--brand-NOMEDAEMPRESA`
- [ ] **CSS `.text-brand-`** (± linha 656): adicionou a classe de cor
- [ ] **CSS `.text-brand-`** (± linha 1191): adicionou com `!important`
- [ ] **CSS `.hover-brand-`** (± linha 2026): adicionou hover do header
- [ ] **Header Desktop** (± linha 2067): adicionou link antes de "Contato"
- [ ] **Header Mobile** (± linha 2111): adicionou link antes de "Contato"
- [ ] **Card Portfólio** (± linha 2475): adicionou novo card
- [ ] **Footer** (± linha 4334): adicionou na lista de marcas
- [ ] **Texto SEO** (± linha 4264): atualizou o h2
- [ ] **Meta Description** (linha 18): atualizou o `<meta name="description">`

---

## 🎨 Referência das Empresas Atuais

| Empresa | Classe CSS | Cor HEX | URL da Página |
|---|---|---|---|
| Weck | `brand-weck` | `#ff7802` | `/representante-weck/` |
| Tecnocuba | `brand-tecnocuba` | `#ff161f` | `/representante-tecnocuba/` |
| Multiflon | `brand-multiflon` | `#981440` | `/representante-multiflon/` |
| Cerâmica Regina | `brand-regina` | `#fad112` | `/representante-ceramica-regina/` |

---

## 💡 Exemplo Completo: Adicionando "Tramontina"

| Campo | Valor |
|---|---|
| `NOMEDAEMPRESA` | `tramontina` |
| `NOMEDISPLAY` | `Tramontina` |
| `NOMEDISPLAY_UPPER` | `TRAMONTINA` |
| `#CORDA_EMPRESA` | `#E4002B` |
| `DESCRICAO_CURTA` | `Linha de Utensílios Domésticos e Profissionais` |
| `IMAGEM_LOGO` | `/imagens-home/tramontina-logo.webp` |
| URL da página | `/representante-tramontina/` |

> **⚠️ IMPORTANTE sobre Responsividade:** Todos os trechos de código acima já são 100% responsivos. O grid de cards usa `grid-cols-1 md:grid-cols-2 lg:grid-cols-4` que se adapta automaticamente. O header mobile é um menu separado com display flex-col. Nenhum ajuste adicional de responsividade é necessário ao adicionar uma nova empresa.
