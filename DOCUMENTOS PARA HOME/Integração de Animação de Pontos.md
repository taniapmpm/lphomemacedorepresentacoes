# Integração de Animação de Pontos em Movimento - Guia Técnico

## Visão Geral

Este documento fornece instruções detalhadas para integrar uma animação de pontos em movimento suave como background em uma Hero Section. A animação utiliza **Three.js** (biblioteca WebGL) para renderizar pontos que se movem em padrões de ondas sinusoidais fluidas. Os pontos serão renderizados em **cinza claro (#C6C6C6)** para contrastar perfeitamente com um fundo azul.

---

## Requisitos Técnicos

### Dependências Necessárias

A única dependência externa necessária é a biblioteca **Three.js**. Você deve incluir a seguinte linha no seu arquivo HTML:

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
```

Alternativamente, se estiver usando um gerenciador de pacotes (npm, yarn, pnpm), instale com:

```bash
npm install three
# ou
yarn add three
# ou
pnpm add three
```

---

## Estrutura do Código

### 1. HTML - Estrutura Base

Adicione um container `<div>` no seu HTML onde a animação será renderizada. Este container deve estar **dentro** ou **atrás** da sua Hero Section:

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sua Página</title>
    <style>
        /* Seu CSS aqui */
    </style>
</head>
<body>
    <!-- Container para a animação Three.js -->
    <div id="canvas-container" style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; z-index: 1;"></div>

    <!-- Sua Hero Section com z-index maior -->
    <section class="hero" style="position: relative; z-index: 10;">
        <!-- Seu conteúdo aqui -->
    </section>

    <!-- Script Three.js -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    
    <!-- Seu script de animação -->
    <script>
        // Código da animação aqui
    </script>
</body>
</html>
```

### 2. CSS - Estilos Necessários

Certifique-se de que o container da animação e a Hero Section estejam posicionados corretamente:

```css
body {
    margin: 0;
    padding: 0;
    overflow: hidden;
    background-color: #your-blue-color; /* Sua cor azul */
}

#canvas-container {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: 1;
    pointer-events: none; /* Permite interação com elementos acima */
}

.hero {
    position: relative;
    z-index: 10;
    width: 100%;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: rgba(your-blue-color, 0.9); /* Fundo azul semi-transparente */
}
```

---

## Código JavaScript - Animação Completa

### Implementação Passo a Passo

Copie e cole o código abaixo na tag `<script>` do seu arquivo HTML. Este código cria a animação de pontos em movimento:

```javascript
// Verificar se Three.js está carregado
if (typeof THREE === 'undefined') {
    console.error('Three.js não foi carregado. Verifique o script tag.');
}

// Configurações da animação
const SEPARATION = 150;
const AMOUNTX = 40;
const AMOUNTY = 60;
const POINT_COLOR = '#C6C6C6'; // Cinza claro
const BACKGROUND_COLOR = '#1a3a52'; // Ajuste para sua cor azul

// Referências para limpeza
let scene, camera, renderer, animationId, count = 0;

function initScene() {
    // Obter container
    const container = document.getElementById('canvas-container');
    if (!container) {
        console.error('Container #canvas-container não encontrado no HTML');
        return;
    }

    // Criar cena
    scene = new THREE.Scene();
    scene.background = new THREE.Color(BACKGROUND_COLOR);
    scene.fog = new THREE.Fog(BACKGROUND_COLOR, 2000, 10000);

    // Criar câmera
    camera = new THREE.PerspectiveCamera(
        60,
        window.innerWidth / window.innerHeight,
        1,
        10000
    );
    camera.position.set(0, 355, 1220);

    // Criar renderer
    renderer = new THREE.WebGLRenderer({
        alpha: true,
        antialias: true,
    });
    renderer.setPixelRatio(window.devicePixelRatio);
    renderer.setSize(window.innerWidth, window.innerHeight);
    renderer.setClearColor(BACKGROUND_COLOR, 1);

    container.appendChild(renderer.domElement);

    // Criar geometria dos pontos
    const positions = [];
    const colors = [];
    const geometry = new THREE.BufferGeometry();

    // Gerar posições dos pontos em grade
    for (let ix = 0; ix < AMOUNTX; ix++) {
        for (let iy = 0; iy < AMOUNTY; iy++) {
            const x = ix * SEPARATION - (AMOUNTX * SEPARATION) / 2;
            const y = 0; // Será animado
            const z = iy * SEPARATION - (AMOUNTY * SEPARATION) / 2;

            positions.push(x, y, z);

            // Converter cor hexadecimal para RGB normalizado (0-1)
            const colorHex = parseInt(POINT_COLOR.replace('#', ''), 16);
            const r = (colorHex >> 16) & 255;
            const g = (colorHex >> 8) & 255;
            const b = colorHex & 255;

            colors.push(r / 255, g / 255, b / 255);
        }
    }

    geometry.setAttribute(
        'position',
        new THREE.Float32BufferAttribute(positions, 3)
    );
    geometry.setAttribute('color', new THREE.Float32BufferAttribute(colors, 3));

    // Criar material
    const material = new THREE.PointsMaterial({
        size: 8,
        vertexColors: true,
        transparent: true,
        opacity: 0.7,
        sizeAttenuation: true,
    });

    // Criar objeto de pontos
    const points = new THREE.Points(geometry, material);
    scene.add(points);

    // Iniciar animação
    animate();

    // Lidar com redimensionamento da janela
    window.addEventListener('resize', onWindowResize);
}

function animate() {
    animationId = requestAnimationFrame(animate);

    // Obter atributo de posição
    const positionAttribute = scene.children[0].geometry.attributes.position;
    const positions = positionAttribute.array;

    // Atualizar posição Y dos pontos com ondas sinusoidais
    let i = 0;
    for (let ix = 0; ix < AMOUNTX; ix++) {
        for (let iy = 0; iy < AMOUNTY; iy++) {
            const index = i * 3;

            // Calcular movimento suave em ondas
            positions[index + 1] =
                Math.sin((ix + count) * 0.3) * 50 +
                Math.sin((iy + count) * 0.5) * 50;

            i++;
        }
    }

    positionAttribute.needsUpdate = true;

    // Renderizar cena
    renderer.render(scene, camera);

    // Incrementar contador para próximo frame
    count += 0.1;
}

function onWindowResize() {
    camera.aspect = window.innerWidth / window.innerHeight;
    camera.updateProjectionMatrix();
    renderer.setSize(window.innerWidth, window.innerHeight);
}

function cleanup() {
    if (animationId) {
        cancelAnimationFrame(animationId);
    }

    if (scene && renderer) {
        scene.traverse((object) => {
            if (object instanceof THREE.Points) {
                object.geometry.dispose();
                if (Array.isArray(object.material)) {
                    object.material.forEach((material) => material.dispose());
                } else {
                    object.material.dispose();
                }
            }
        });

        renderer.dispose();

        const container = document.getElementById('canvas-container');
        if (container && renderer.domElement) {
            container.removeChild(renderer.domElement);
        }
    }

    window.removeEventListener('resize', onWindowResize);
}

// Inicializar quando o DOM estiver pronto
if (document.readyState === 'loading') {
    document.addEventListener('DOMContentLoaded', initScene);
} else {
    initScene();
}

// Limpeza ao descarregar a página
window.addEventListener('beforeunload', cleanup);
```

---

## Parametrização da Animação

### Variáveis Configuráveis

Você pode ajustar os seguintes parâmetros para customizar a animação:

| Parâmetro | Valor Padrão | Descrição |
|-----------|--------------|-----------|
| `SEPARATION` | 150 | Distância entre pontos na grade (em pixels) |
| `AMOUNTX` | 40 | Número de pontos no eixo X |
| `AMOUNTY` | 60 | Número de pontos no eixo Y |
| `POINT_COLOR` | #C6C6C6 | Cor dos pontos em hexadecimal |
| `BACKGROUND_COLOR` | #1a3a52 | Cor de fundo em hexadecimal |

### Ajustar Velocidade da Animação

Para modificar a velocidade dos pontos, altere o incremento de `count` na função `animate()`:

```javascript
// Mais rápido (aumente o valor)
count += 0.15; // Mais rápido que o padrão

// Mais lento (diminua o valor)
count += 0.05; // Mais lento que o padrão
```

### Ajustar Amplitude das Ondas

Para modificar a altura das ondas, altere os multiplicadores na função `animate()`:

```javascript
// Ondas maiores
positions[index + 1] =
    Math.sin((ix + count) * 0.3) * 100 +  // Aumentado de 50 para 100
    Math.sin((iy + count) * 0.5) * 100;

// Ondas menores
positions[index + 1] =
    Math.sin((ix + count) * 0.3) * 25 +   // Diminuído de 50 para 25
    Math.sin((iy + count) * 0.5) * 25;
```

---

## Integração com Sua Página Existente

### Passo 1: Adicionar o Container

Adicione este HTML **no início** do seu arquivo, antes da Hero Section:

```html
<div id="canvas-container"></div>
```

### Passo 2: Adicionar CSS

Adicione estes estilos ao seu CSS:

```css
#canvas-container {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: 1;
    pointer-events: none;
}

body {
    overflow: hidden;
}
```

### Passo 3: Adicionar Script Three.js

Adicione esta linha **antes** do seu script de animação:

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
```

### Passo 4: Adicionar o Script de Animação

Copie o código JavaScript completo fornecido na seção anterior e adicione em uma tag `<script>` no seu arquivo HTML.

### Passo 5: Ajustar z-index

Certifique-se de que sua Hero Section tem `z-index` maior que 1:

```css
.hero {
    position: relative;
    z-index: 10;
}
```

---

## Solução de Problemas

### A animação não aparece

**Possíveis causas:**
- Three.js não foi carregado corretamente. Verifique o console do navegador (F12) para erros.
- O container `#canvas-container` não existe no HTML.
- O `z-index` da Hero Section é menor que o do container da animação.

**Solução:**
Verifique o console do navegador e procure por mensagens de erro. Certifique-se de que todas as etapas de integração foram seguidas.

### Os pontos aparecem, mas não se movem

**Possível causa:**
A função `animate()` não está sendo chamada ou `requestAnimationFrame` não está funcionando.

**Solução:**
Verifique se o script foi adicionado corretamente e se não há erros no console.

### Os pontos têm cor errada

**Possível causa:**
O valor de `POINT_COLOR` está incorreto ou não foi atualizado.

**Solução:**
Altere o valor de `POINT_COLOR` para `'#C6C6C6'` (cinza claro) ou qualquer outra cor desejada em formato hexadecimal.

### Performance ruim ou lag

**Possíveis causas:**
- Muitos pontos (valores altos de `AMOUNTX` e `AMOUNTY`).
- Dispositivo com GPU fraca.

**Solução:**
Reduza os valores de `AMOUNTX` e `AMOUNTY` para diminuir o número de pontos renderizados. Por exemplo, altere para `AMOUNTX = 30` e `AMOUNTY = 40`.

---

## Exemplo Completo de Arquivo HTML/CSS/JS Único

Aqui está um exemplo completo de como estruturar seu arquivo único:

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Página com Animação de Pontos</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #1a3a52;
            overflow: hidden;
            height: 100vh;
        }

        #canvas-container {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 1;
            pointer-events: none;
        }

        .hero {
            position: relative;
            z-index: 10;
            width: 100%;
            height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            background-color: rgba(26, 58, 82, 0.85);
            color: white;
            text-align: center;
        }

        .hero h1 {
            font-size: 3rem;
            margin-bottom: 1rem;
        }

        .hero p {
            font-size: 1.2rem;
            max-width: 600px;
        }
    </style>
</head>
<body>
    <!-- Container para animação Three.js -->
    <div id="canvas-container"></div>

    <!-- Hero Section -->
    <section class="hero">
        <div>
            <h1>Bem-vindo</h1>
            <p>Animação de pontos em movimento suave como background</p>
        </div>
    </section>

    <!-- Script Three.js -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>

    <!-- Script de Animação -->
    <script>
        // [Copie o código JavaScript completo aqui]
    </script>
</body>
</html>
```

---

## Notas Importantes

### Compatibilidade

A animação utiliza **WebGL** através do Three.js, que é suportado em todos os navegadores modernos (Chrome, Firefox, Safari, Edge). Para navegadores muito antigos, a animação pode não funcionar.

### Performance

A animação é otimizada para performance, mas em dispositivos com GPU fraca, você pode notar redução de frames. Neste caso, reduza o número de pontos (`AMOUNTX` e `AMOUNTY`).

### Acessibilidade

A animação é apenas visual e não afeta a acessibilidade da página. Certifique-se de que o conteúdo da Hero Section seja legível sobre o background animado.

---

## Suporte Adicional

Se encontrar problemas durante a integração, verifique:

1. **Console do navegador** (F12) para mensagens de erro
2. **Estrutura HTML** - certifique-se de que o container existe
3. **Ordem dos scripts** - Three.js deve ser carregado antes do script de animação
4. **Valores de configuração** - verifique se as cores e parâmetros estão corretos

---

**Documento preparado para integração com Antigravity AI**

Data: 04 de Maio de 2026  
Versão: 1.0  
Tecnologia: Three.js WebGL
