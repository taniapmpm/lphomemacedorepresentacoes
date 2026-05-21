PROMPT — PÁGINA HOME
S. MACEDO NEGÓCIOS E REPRESENTAÇÕES LTDA.

Leia com atenção os arquivos design-system.md e contexto-projeto.md que estou anexando. Eles contêm o padrão visual, técnico e de identidade da marca. Este prompt cria a página Home do site, que é diferente das páginas de empresa: ela apresenta o Sílvio Macedo como representante comercial e tem como objetivo converter empresas que buscam contratar um representante em São Paulo.

---

DADOS DA PÁGINA

- Página: Home — S. Macedo Negócios e Representações Ltda.
- URL: macedorepresentacoes.com.br
- ID do container: page-container-home
- Pasta de imagens — logos e marcas padrão: /imagenspadrao/
- Pasta de imagens — específicas desta página: /imagens_home/
- Prefixo CSS: mr-home-
- Cor de destaque desta página: #19546B (petroleum — cor própria da S. Macedo, sem empresa representada)
- Webhook Make.com contato: URL_WEBHOOK_CONTATO_HOME
- Tipo no payload: "contato HOME"

---

LOGO E IMAGENS PADRÃO

- Logo S. Macedo (navbar e footer): /imagenspadrao/logo-sm.png — 56x56px, nunca substituir por placeholder
- Logo das empresas representadas (seção de portfólio): /imagenspadrao/logo-weck.jpg, /imagenspadrao/logo-tecnocuba.jpg, /imagenspadrao/logo-multiflon.jpg, /imagenspadrao/logo-ceramica-regina.jpg
- Logos dos clientes atendidos: /imagenspadrao/cliente-rebal.jpg, /imagenspadrao/cliente-maquinbal.jpg, /imagenspadrao/cliente-upcasa.jpg, /imagenspadrao/cliente-utiliplast.jpg, /imagenspadrao/cliente-kofisa.jpg, /imagenspadrao/cliente-pracasanet.jpg
- Imagem de fundo de personalização da página (textura/fundo): /imagenspadrao/inspiracao-fundo.jpg — usar como fundo decorativo sutil em seções selecionadas para dar identidade visual à página home
- Imagens específicas desta página: /imagens_home/ — deixar os src dos elementos img vazios com o atributo alt descritivo. Exemplo: src="" alt="Sílvio Macedo representante comercial São Paulo". Não usar placeholders, não mockar.

---

OBJETIVO DA PÁGINA

O visitante-alvo é um empresário, diretor comercial ou gestor que avalia a contratação de um representante comercial. A página deve demonstrar competência técnica, cobertura de mercado, uso de tecnologia e histórico de resultados. Cada seção responde a uma questão objetiva desse perfil de visitante.

O tom é profissional e direto. Linguagem B2B. Sem promessas genéricas.

---

ESTRUTURA DE SEÇÕES

SEÇÃO 1 — NAVBAR
Replicar exatamente a navbar das páginas Weck e Tecnocuba conforme design-system.md.
- Logo: /imagenspadrao/logo-sm.png
- Nome: S.Macedo Negócios e Representações Ltda.
- Badge: sem badge de empresa (esta é a página da marca pessoal)
- Links do menu: HOME, WECK, TECNOCUBA, MULTIFLON, CERÂMICA REGINA, CONTATO
- Botão telefone: (11) 98712-2890
- Scroll effect: py-9 reduz para py-5 ao rolar

SEÇÃO 2 — HERO
- Fundo: navy #0D1F30 com a imagem /imagenspadrao/inspiracao-fundo.jpg aplicada como overlay sutil (opacity baixa, blend-mode multiply ou similar) para dar textura sem comprometer a legibilidade
- H1: Representante Comercial Estratégico em São Paulo
- Subtítulo: Mais de 30 anos conectando empresas ao mercado paulista com estrutura comercial, tecnologia e atendimento especializado.
- Dois botões CTA: primário "Empresas que Represento" (âncora para seção de portfólio), secundário "Fale Comigo" (âncora para contato)
- Stats (3 números): +500 Clientes Ativos | +15 Municípios | SP Estado de Atuação
- Card branco flutuante com logo /imagenspadrao/logo-sm.png em destaque, igual ao modelo das páginas de empresa

SEÇÃO 3 — MARQUEE
Faixa dark animada em loop com os seguintes avisos:
- REPRESENTAÇÃO COMERCIAL B2B
- ATENDIMENTO EM TODO O ESTADO DE SÃO PAULO
- MAIS DE 30 ANOS DE MERCADO
- VISITAS PRESENCIAIS E AMOSTRAS
- MAPA GEO-LOCALIZADO DE CLIENTES
- ANÚNCIOS META ADS
(duplicar todos para loop contínuo)

SEÇÃO 4 — PORTFÓLIO DE MARCAS
- Eyebrow: EMPRESAS QUE REPRESENTO
- Título H2: Marcas com Presença Nacional
- Subtítulo: Portfólio selecionado para atender lojistas, atacadistas, redes de varejo e distribuidores em todo o Estado de São Paulo.
- 4 cards, grid 2x2 ou linha de 4, cada card com: logo da empresa (src conforme listado acima), nome, linha de produto, botão "Conhecer" linkando para a página da empresa
  - Weck | Linha Utilitária Doméstica e Profissional | /representante-weck/
  - Tecnocuba | Linha Inox Gastronômica e Construção Civil | /representante-tecnocuba/
  - Multiflon | Linha Panelas e Formas | /representante-multiflon/
  - Cerâmica Regina | (linha a preencher) | /representante-ceramica-regina/
- Cards com hover scale e shadow conforme padrão do design-system.md

SEÇÃO 5 — DIFERENCIAIS COMPETITIVOS
- Eyebrow: POR QUE A S. MACEDO
- Título H2: O que diferencia este representante
- 6 cards em grid 3x2, com ícone Lucide, título e descrição objetiva:
  1. Experiência de Mercado — Mais de 30 anos de atuação no segmento B2B, com profundo conhecimento dos canais de distribuição em São Paulo.
  2. Carteira Ativa — Base consolidada de lojistas, atacadistas, redes de varejo e distribuidores ativos em todo o Estado.
  3. Tecnologia Aplicada — Uso de mapa geo-localizado, Meta Ads e consultoria comercial para ampliar o alcance das marcas representadas.
  4. Atendimento Presencial — Visitas regulares, apresentação de amostras e acompanhamento próximo de cada cliente.
  5. Cobertura Estadual — Presença em mais de 15 municípios com planejamento de rotas e logística de atendimento.
  6. Resultados Mensuráveis — Acompanhamento de indicadores por marca e por canal, com relatórios e feedback periódico.

SEÇÃO 6 — METODOLOGIA DE TRABALHO
- Eyebrow: COMO TRABALHAMOS
- Título H2: Da prospecção ao resultado
- 4 passos numerados (01 a 04), visual identico às páginas de empresa:
  01 | Conhecimento do produto — Estudo da marca, portfólio, posicionamento e condições comerciais antes de qualquer contato com o mercado.
  02 | Mapeamento de canais — Identificação dos clientes ideais por segmento, região e perfil de compra.
  03 | Execução em campo — Visitas presenciais, entrega de amostras, negociação e fechamento com acompanhamento ativo.
  04 | Monitoramento — Acompanhamento de pedidos, relacionamento pós-venda e expansão da carteira.
- Fundo navy #0D1F30

SEÇÃO 7 — FERRAMENTAS E TECNOLOGIA
- Eyebrow: TECNOLOGIA
- Título H2: Estrutura digital a serviço das vendas
- 3 cards com imagem (src vazio, alt descritivo), título e descrição:
  1. Mapa Geo-Localizado | src="" alt="Mapa geo-localizado de clientes São Paulo" | Visualização da carteira de clientes por região, facilitando o planejamento de rotas e a identificação de oportunidades.
  2. Anúncios Meta Ads | src="" alt="Gestão de anúncios Meta Ads para representação comercial" | Campanhas segmentadas no Facebook e Instagram para ampliar a visibilidade das marcas representadas junto ao público B2B.
  3. Consultoria Comercial | src="" alt="Consultoria comercial e estratégia de vendas" | Análise de mercado, estratégia de precificação e suporte na tomada de decisão comercial para as empresas representadas.
- Imagens na pasta /imagens_home/

SEÇÃO 8 — CLIENTES ATENDIDOS
- Eyebrow: NOSSOS CLIENTES
- Título H2: Empresas que confiam na S. Macedo
- Frase de apoio: Parceiros consolidados em diferentes segmentos do varejo e da distribuição.
- Faixa de logos em marquee horizontal com loop contínuo (CSS puro, sem JS):
  /imagenspadrao/cliente-rebal.jpg
  /imagenspadrao/cliente-maquinbal.jpg
  /imagenspadrao/cliente-upcasa.jpg
  /imagenspadrao/cliente-utiliplast.jpg
  /imagenspadrao/cliente-kofisa.jpg
  /imagenspadrao/cliente-pracasanet.jpg
  (duplicar para loop contínuo)

SEÇÃO 9 — CTA DE CONVERSÃO
- Fundo: navy #0D1F30, com overlay sutil da imagem /imagenspadrao/inspiracao-fundo.jpg
- Título H2: Sua empresa precisa de representação comercial em São Paulo?
- Parágrafo: Atendemos todo o Estado com estrutura, experiência e comprometimento. Conheça as marcas que representamos ou entre em contato diretamente.
- Dois botões: "Ver Empresas Representadas" (âncora portfólio) e "Entrar em Contato" (âncora contato)
- Visual de alto impacto, texto centralizado

SEÇÃO 10 — INSTAGRAM
- Título H2: Acompanhe no Instagram
- Exibir o QR Code (src="" alt="QR Code Instagram macedorepresentacoes_01") — imagem na pasta /imagens_home/
- Nome de usuário: @macedorepresentacoes_01
- Link: https://www.instagram.com/macedorepresentacoes_01
- Botão "Seguir no Instagram"

SEÇÃO 11 — FORMULÁRIO DE CONTATO
- Eyebrow: CONTATO
- Título H2: Fale com a S. Macedo
- Subtítulo: Fale conosco para saber mais sobre representação ou solicitar informações.
- Formulário idêntico ao das páginas Weck e Tecnocuba — mesmo código, mesma estrutura, mesmas máscaras (CNPJ, WhatsApp), mesmo envio via XMLHttpRequest para webhook Make.com.
- Campos: Nome, CNPJ, E-mail, WhatsApp, Mensagem.
- Botão: Enviar Mensagem
- Webhook: URL_WEBHOOK_CONTATO_HOME
- Tipo no payload: "contato HOME"
- Ao lado do formulário: dados de contato direto — telefone (11) 98712-2890, e-mail silviomacedo.negocios@gmail.com, Instagram @macedorepresentacoes_01, LinkedIn linkedin.com/in/silviomacedo01

SEÇÃO 12 — TEXTO SEO
- Título H2: Representante Comercial em São Paulo — Weck, Tecnocuba, Multiflon e Cerâmica Regina
- Parágrafo de aproximadamente 150 palavras com linguagem natural e palavras-chave relevantes: representante comercial São Paulo, representação B2B, utensílios profissionais, cubas inox, panelas e formas, distribuidores, lojistas, atacadistas, Estado de São Paulo.
- Visual discreto, sem destaque excessivo.

SEÇÃO 13 — FOOTER
Replicar o footer das páginas Weck e Tecnocuba conforme design-system.md, com as seguintes atualizações:
- Coluna 1: Logo /imagenspadrao/logo-sm.png, nome S.Macedo Negócios e Representações Ltda., redes sociais Instagram e LinkedIn
- Coluna 2 — Marcas Representadas: Weck, Tecnocuba, Multiflon, Cerâmica Regina — com links para as respectivas páginas
- Coluna 3 — Navegação: links âncora das seções desta página (Home, Empresas, Diferenciais, Como Trabalhamos, Clientes, Contato) + Política de Privacidade + Termos de Uso
- Coluna 4 — Contato Direto: cards de WhatsApp e e-mail
- Rodapé final: S. Macedo Representações © 2025. Todos os Direitos Reservados.
- Linha decorativa no topo do footer: petroleum #19546B (cor desta página)

---

ESPECIFICAÇÕES TÉCNICAS

FRAMEWORK E DEPENDÊNCIAS
- Tailwind CSS via CDN: https://cdn.tailwindcss.com
- Lucide Icons via CDN: https://unpkg.com/lucide@latest
- Sem outros frameworks ou bibliotecas externas

IMAGENS
- Imagens de logos e padrão: /imagenspadrao/
- Imagens específicas desta página: /imagens_home/
- Não usar placeholders. Deixar src="" com alt descritivo em todas as imagens da pasta /imagens_home/ que ainda não existem.
- Logos e clientes já têm caminho definido — usar exatamente como especificado acima.
- Imagens de produto/seção: proporção 4:3, 800x600px
- Banner hero e CTA: proporção 2:1, 1280x640px
- Logos: 400x200px exibido
- Logo S. Macedo (navbar/footer): 56x56px
- Definir width e height em todos os elementos img para evitar CLS
- Lazy loading (loading="lazy") em todas as imagens abaixo da dobra
- Preload na imagem de fundo do hero

RESPONSIVIDADE
- Breakpoints: mobile 375px, tablet 768px, desktop 1280px
- Font-size mínimo 16px em inputs (evitar zoom automático iOS)
- overflow-x: hidden no wrapper da página (não no body global)
- Todos os grids colapsam corretamente em mobile

JAVASCRIPT
- Replicar exatamente o mesmo bloco JS das páginas Weck e Tecnocuba:
  lucide.createIcons()
  enviarWebhook() via XMLHttpRequest
  Scroll effect navbar
  Toggle menu mobile
  Smooth scroll âncoras
  IntersectionObserver para fade-in (.js-scroll-anim)
  Máscaras CNPJ e WhatsApp
  Marquee de logos de clientes via CSS puro (sem JS)
  Prefetch inteligente de imagens na navbar

ISOLAMENTO DE ESTILOS
- ID do container: page-container-home
- Prefixo CSS: mr-home- em todas as classes customizadas
- Nenhum seletor genérico deve vazar para fora do container
- Remover ou renomear qualquer classe reservada do WordPress ou Elementor: content, main, header, footer, container, row, col, btn, wrap, wrapper, entry, post

SEO
- Title: Representante Comercial em São Paulo | S. Macedo Negócios e Representações
- H1 único na hero
- H2 nos títulos de seção
- H3 nos subtítulos e nomes de cards
- HTML semântico: section, article, nav, header, footer, main

CORES CSS (variáveis)
--brand-navy: #0D1F30
--brand-petroleum: #19546B
--brand-accent: #19546B (esta página usa petroleum como destaque, sem empresa representada)
--brand-white: #FFFFFF
--brand-neutral: #C6C6C6
--brand-gray: #706F6F
--footer-bg: #0d1b2a

WEBHOOK
var WEBHOOK_MAKE = 'URL_WEBHOOK_CONTATO_HOME';
Payload: { tipo: "solicitação de representante", nome, cnpj, email, whatsapp, mensagem, data_envio }

---

ENTREGA

Entregar o HTML completo em um único arquivo, pronto para colar no widget HTML do Elementor.
CSS em bloco style no topo do arquivo.
JavaScript ao final, antes do fechamento do div container principal.
Comentário no topo do arquivo:

Página: Home — S. Macedo Negócios e Representações Ltda.
Versão: 1.0
Container ID: page-container-home
Prefixo CSS: mr-home-
Pasta imagens padrão: /imagenspadrao/
Pasta imagens específicas: /imagens_home/
Webhook: URL_WEBHOOK_CONTATO_HOME

---

CHECKLIST FINAL (verificar antes de entregar)

ID page-container-home aplicado no wrapper principal.
Prefixo mr-home- em todas as classes CSS customizadas.
Nenhum seletor genérico vazando para fora do container.
Navbar com menu atualizado: HOME, WECK, TECNOCUBA, MULTIFLON, CERÂMICA REGINA, CONTATO.
Logo /imagenspadrao/logo-sm.png no header e footer — nunca substituída por placeholder.
Logos das empresas representadas e clientes com caminhos corretos em /imagenspadrao/.
Imagens de /imagens_home/ com src="" e alt descritivo — sem placeholders.
Imagem de fundo /imagenspadrao/inspiracao-fundo.jpg usada na hero e na seção CTA.
Formulário com XMLHttpRequest para webhook, campos com máscaras, campo CNPJ obrigatório.
Footer com 4 colunas, cor decorativa petroleum, link Cerâmica Regina incluído.
Marquee de clientes com CSS puro, sem JS.
JavaScript idêntico ao das páginas Weck e Tecnocuba.
H1 único na hero.
Hierarquia H1, H2, H3 correta.
overflow-x hidden no container, não no body global.
Font-size mínimo 16px em inputs.
Lazy loading em imagens abaixo da dobra.
Preload na imagem de fundo da hero.
Width e height definidos em todos os elementos img.
Responsivo em mobile 375px, tablet 768px, desktop 1280px.
Variáveis CSS com os valores corretos para esta página.
Payload do webhook com tipo "contato HOME".
