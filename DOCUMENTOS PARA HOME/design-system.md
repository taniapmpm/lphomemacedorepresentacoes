# DESIGN SYSTEM — S. Macedo Representações
> Extraído da página Weck (página modelo) **e do Manual de Identidade Visual oficial (Playbook)**. Use este arquivo como referência visual obrigatória para todas as novas páginas.

---

## 1. ESTRUTURA TÉCNICA

- **Framework CSS:** Tailwind CSS via CDN (`https://cdn.tailwindcss.com`)
- **Ícones:** Lucide Icons via CDN (`https://unpkg.com/lucide@latest`)
- **Onde o código vai:** Elementor > bloco HTML tag > colar o HTML completo
- **Hospedagem:** Hostinger
- **Importante:** Todo CSS fica dentro de `<style>` no próprio arquivo. Sem arquivos externos criados por você.
- **Container principal:** `<div id="page-container-[SIGLA-DA-EMPRESA]">` — o ID muda por empresa para isolar estilos.

---

## 2. PALETA DE CORES

### ✅ PALETA OFICIAL — Manual de Identidade Visual S. Macedo

Estas são as cores extraídas diretamente do Playbook oficial. Devem ser usadas em todas as páginas sem alteração.

```
NAVY (primária):    #0D1F30   → fundo escuro, navbar, seções dark, textos
                               Playbook: C100 M80 Y50 K65

PETROLEUM (secundária): #19546B → destaque, hover, seções médias
                                   Playbook: C90 M50 Y35 K30

BRANCO:             #FFFFFF   → fundos claros, textos em fundos escuros
                               Playbook: C0 M0 Y0 K0

PRETO:              #000000   → uso em materiais impressos
                               Playbook: C0 M0 Y0 K100

CINZA CLARO:        #C6C6C6   → bordas, textos secundários, neutros
                               Playbook: C0 M0 Y0 K30

CINZA MÉDIO:        #706F6F   → textos apagados, rodapés
                               Playbook: C0 M0 Y0 K70
```

### Cor de destaque (muda por empresa — é a cor da marca representada):
```
--brand-accent: #e8520a   → COR DA WECK (laranja, não faz parte do playbook da S. Macedo)
```
> Para cada nova empresa, esta cor é substituída pela cor principal da marca.
> A S. Macedo não tem cor de destaque própria — ela adota a cor da empresa representada como acento.
> Exemplos: se for azul → `#0057B8`, se for verde → `#00A651`

### Cores de fundo das seções:
```
Branco:      #FFFFFF   → seções principais (categorias, produtos)
Cinza claro: #F9FAFB   → seções alternadas
Navy:        #0D1F30   → seções de destaque/CTA
Footer:      #0d1b2a   → footer sempre escuro (variação mais escura do navy)
```

---

## 3. TIPOGRAFIA

### ✅ FONTE OFICIAL — Manual de Identidade Visual S. Macedo

```
OPEN SANS — Família tipográfica oficial da marca S. Macedo
(Playbook pág. 13: "A família Open Sans possui diversas variedades de pesos.
Priorize sempre as descritas nesse documento.")

Open Sans Light   → legendas, textos de apoio
Open Sans Regular → corpo de texto, parágrafos
Open Sans Bold    → títulos, destaques, headings
```

### Fontes complementares usadas nas páginas (além da oficial):
> A Open Sans é a fonte da marca. Nas páginas das empresas, fontes extras foram adicionadas para criar hierarquia visual mais rica no contexto digital.

```
Space Grotesk  → títulos H1, H2, H3, H4 (font-display, font-black) — hierarquia de impacto
Inter          → parágrafos, spans, links — leitura fluida
DM Sans        → footer
DM Mono        → labels uppercase no footer
Bebas Neue     → nomes das marcas no footer
```

> **Regra:** Em dúvida, use Open Sans Bold para títulos e Open Sans Regular para corpo. As fontes complementares são para contexto digital apenas.

### Hierarquia de tamanhos (desktop):
```
Hero H1:    text-6xl  (3.75rem) — font-black, tracking-tight
Seção H2:  text-5xl  (3rem)    — font-black
Card H4:   text-lg/xl           — font-bold
Eyebrow:   text-xs, uppercase, tracking-widest, cor brand-accent (cor da empresa)
Parágrafo: text-base/sm, text-brand-navy/60 ou white/60
```

---

## 4. ESTRUTURA DE SEÇÕES (ordem padrão de todas as páginas)

```
1. NAV           → Navbar fixa, branca, logo + nome + badge da empresa + links + botão telefone
2. HERO          → Fundo navy, headline, botões, logo da empresa em card branco flutuante
3. MARQUEE       → Faixa dark com avisos em loop (ex: "VENDA EXCLUSIVA PARA CNPJ")
4. LANÇAMENTOS   → Carrossel de banners 2:1 com auto-play a cada 4s
5. CATEGORIAS    → Grid 3 colunas, cards com imagem + gradiente + título sobreposto
6. PRODUTOS      → Grid 3 colunas, cards com imagem, título e descrição embaixo
7. CTA DARK      → Seção navy com headline centralizado e parágrafo
8. CARROSSEL     → Faixa de imagens em loop infinito (marquee)
9. COMO COMPRAR  → 4 passos numerados (01 a 04) em fundo navy
10. CATÁLOGO     → Seção petroleum com formulário de solicitação + 6 cards de benefícios
11. CONTATO      → Formulário completo + dados de contato
12. FOOTER       → 4 colunas: marca, marcas representadas, navegação, contato
13. MODAL        → Pop-up de solicitação de catálogo (ativado por botão)
```

---

## 5. COMPONENTES REUTILIZÁVEIS

### Navbar
- Fundo: `bg-white/95 backdrop-blur-xl`
- Logo: imagem circular + nome "S. Macedo Negócios e Representações Ltda."
- Badge da empresa atual: retângulo `bg-brand-[COR]` com nome da empresa em uppercase
- Links: uppercase, tracking-[0.15em], com underline animado no hover
- Botão telefone: `bg-brand-navy`, hover `bg-brand-petroleum`
- **Scroll effect:** ao rolar, `py-9` vira `py-5` e shadow aumenta

### Botões
```
Primário:   bg-brand-[COR] text-white → hover: bg-white text-brand-navy
Secundário: bg-white/10 border border-white/20 text-white → hover: bg-white/20
Formulário: bg-brand-navy text-white → hover: bg-brand-petroleum
```

### Cards de categoria / produto
```
aspect-[4/3], rounded-[32px], overflow-hidden
Imagem: object-contain (categorias) ou object-cover (produtos)
Hover: scale-110 na imagem + shadow-2xl no card
Overlay: gradiente from-black/80 via-black/20 to-transparent
Título: absolute bottom-0, text-white, hover: text-brand-[COR]
```

### Seção eyebrow (label acima do título)
```html
<span class="text-xs font-bold uppercase tracking-widest text-brand-[COR] mb-4 block">
  Texto da eyebrow
</span>
```

### Formulários
```
Campos: bg-brand-neutral/5, border border-brand-neutral/20, rounded-xl, px-6 py-4
Focus: border-brand-orange (substitua pela cor da empresa)
Máscara CNPJ: 00.000.000/0001-00
Máscara WhatsApp: (00) 00000-0000
```

### Marquee (faixa animada)
```css
@keyframes marquee { 0% { transform: translateX(0); } 100% { transform: translateX(-50%); } }
.animate-marquee { display: flex; animation: marquee 30s linear infinite; }
```
> O conteúdo é duplicado (itens repetidos) para o loop ser contínuo.

### Botão flutuante WhatsApp
- Fixo, bottom-8 right-8, z-[100]
- Cor: `#25D366`, hover: `#128C7E`
- Tooltip aparece no hover com `group-hover:opacity-100`

---

## 6. FOOTER (estrutura fixa)

4 colunas:
1. **Marca** → logo, tagline, redes sociais (Instagram + LinkedIn)
2. **Marcas Representadas** → lista das empresas com links para as páginas
3. **Navegação** → links âncora da página atual
4. **Contato Direto** → cards de WhatsApp e e-mail

> Cores do footer sempre fixas (independente da empresa):
```
--footer-bg: #0d1b2a
--footer-accent: #19546b
```
> A linha decorativa no topo do footer usa a cor de destaque da empresa da página.

---

## 7. JAVASCRIPT (funções padrão em todas as páginas)

```
✓ lucide.createIcons()              → ativa os ícones SVG
✓ enviarWebhook(dados)             → envia formulários ao Make.com via XMLHttpRequest
✓ Scroll effect navbar             → py-9 → py-5 ao rolar
✓ Toggle menu mobile               → hambúrguer ↔ X
✓ Smooth scroll âncoras            → scrollIntoView({ behavior: 'smooth' })
✓ Modal catálogo                   → abre/fecha, submit envia webhook
✓ Carrossel lançamentos            → auto-play 4s, indicadores clicáveis
✓ IntersectionObserver             → fade-in ao entrar na viewport (.js-scroll-anim)
✓ Máscaras CNPJ e WhatsApp        → formatação automática nos inputs
✓ Prefetch inteligente             → lazy images viram eager ao hover nos links da nav
```

### Webhook Make.com
```javascript
var WEBHOOK_MAKE = 'URL_DO_WEBHOOK_AQUI';
// Payload padrão enviado:
{
  tipo: 'contato NOME-EMPRESA' ou 'catalogo NOME-EMPRESA',
  nome, cnpj, email, whatsapp, mensagem, data_envio
}
```

---

## 8. RESPONSIVIDADE

```
Desktop:  > 1024px  → layout completo
Tablet:   768-1024px → textos reduzidos
Mobile:   < 768px   → grid 2 colunas em categorias e produtos, padding reduzido
Pequeno:  < 380px   → ajustes finos de tamanho
```

---

## 9. IMAGENS

- **Pasta:** `/imagenspagina[sigla]/` — ex: `/imagenspaginawck/`, `/imagenspaginatecnocuba/`
- **Logo navbar + footer:** `logo-sm.png` (56x56px, circular)
- **Logo hero (card branco):** `[empresa]-logo.jpg` (400x400px)
- **Banners carrossel:** proporção 2:1, sugerido 1280x640px
- **Cards categorias/produtos:** proporção 4:3, sugerido 400x300px
- **Carrossel marquee inferior:** 1:1, sugerido 500x500px, 224x224px exibido

---

## 10. LOGO — REGRAS OFICIAIS DO PLAYBOOK

### Versões da marca (Playbook pág. 05–08):
```
Versão Principal:    símbolo circular 3D "S" + nome "S.Macedo Negócios e Representações Ltda."
Versão Secundária:   símbolo circular sozinho (sem o nome)
Versão Positiva:     uso em fundos claros (branco, cinza)
Versão Negativa:     uso em fundos escuros (navy, preto)
```

### Tamanhos mínimos (Playbook pág. 09):
```
Digital:   110px de largura (logo completa) / 30px (só o símbolo)
Impresso:  30mm de largura (logo completa) / 07mm (só o símbolo)
```

### Usos proibidos (Playbook pág. 10):
```
✗ Não comprimir ou esticar a marca
✗ Não alterar as cores da marca
✗ Não adicionar sombra projetada
✗ Não alterar a tipografia dos elementos
✗ Não aplicar em fundos que prejudiquem a leitura
✗ Não adicionar elementos externos à marca
```

### Aplicação sobre fundos (Playbook pág. 11):
```
Fundos claros (azul claro, cinza, branco) → usar versão positiva (cores originais)
Fundos escuros (navy, preto, foto escura) → usar versão negativa (branca)
```

### Na navbar do site:
- Usar logo circular (só o símbolo) com 56x56px
- Sempre com fundo branco na navbar
- Nome "S.Macedo Negócios e Representações Ltda." em Open Sans Bold, cor navy

### ✅ ARQUIVO DA LOGO — ENVIADO JUNTO COM ESTE DOCUMENTO
```
Arquivo:  logo-sm.png
Uso:      header (navbar) e footer de TODAS as páginas
Caminho:  /imagenspaginawck/logo-sm.png  (Weck)
          /imagenspaginatecnocuba/logo-sm.png  (Tecnocuba)
          /imagenspaginamultiflon/logo-sm.png  (Multiflon)
          — copiar o mesmo arquivo para cada pasta de empresa
Tamanho:  56x56px exibido, PNG com fundo transparente ou circular
```
> **Regra:** Nunca substituir por placeholder, ícone genérico ou outro arquivo.
> O arquivo `logo-sm.png` é sempre o símbolo circular da S. Macedo.
> Ele é enviado junto com este pacote de arquivos.

---

## 11. SEO (padrão do `<title>`)

```
Representante [NOME-EMPRESA] SP | [PRODUTO PRINCIPAL] para Revenda no Atacado
```
Exemplo: `Representante Weck SP | Utensílios de Cozinha Profissionais para Revenda no Atacado`
