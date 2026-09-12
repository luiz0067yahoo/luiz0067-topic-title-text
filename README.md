# Luiz0067 Antigravity Prompt / Floating Cards (Topic Title Text)

Plugin WordPress independente que disponibiliza o bloco nativo Gutenberg **"Antigravity Prompt / Floating Cards"** (`luiz0067/topic-title-text`).
Permite a inserção de tópicos flutuantes animados com efeito de **antigravidade** (levitação suave via CSS), compostos por títulos, textos/descrições, tags de prompt e ações interativas (como cópia para área de transferência e links).

---

## Principais Recursos

- 🚀 **Física de Antigravidade (CSS Puro)**:
  - Animação de levitação infinita (`@keyframes antigravity-float`) suave e fluida.
  - Sombra de profundidade no solo sincronizada com a distância de flutuação (`@keyframes antigravity-shadow`).
  - Pausa suave no hover (`:hover`) para facilitar leitura e seleção de conteúdo.
- 🎨 **100% WYSIWYG**:
  - Edição ao vivo no Gutenberg com fidelidade visual idêntica à renderização no frontend.
- 🏷️ **Tags de Prompt & Ações**:
  - Badge personalizável para categorizar o prompt (ex: `PROMPT #01`, `CHATGPT-4`, `CSS3`).
  - Botão de ação integrado para **Copiar Prompt** direto para a área de transferência com notificação visual instantânea (*Toast* "Copiado!") ou redirecionamento de link.
- 🎛️ **Controles Avançados no Inspetor**:
  - Velocidade do ciclo de levitação (em segundos).
  - Delay de início para criar descompasso natural entre múltiplos cards lado a lado.
  - Paleta de cores com geração dinâmica de variáveis CSS (`--ag-color`, `--ag-glow`, `--ag-speed`, `--ag-delay`).
  - 4 temas visuais: **Glassmorphism (Vidro Fosco)**, **Dark Neon**, **Cyber Glow** e **Minimal Clean**.
- ♿ **Acessibilidade & Performance**:
  - Respeita `@media (prefers-reduced-motion: reduce)` para usuários com sensibilidade a movimentos.
  - Zero dependências pesadas, sem necessidade de bundlers ou ferramentas de compilação.
  - Compatível com WordPress 6.0+ e PHP 7.4+.

---

## Padrões Arquiteturais

1. **Sintaxe JavaScript Nativa do WordPress**:
   - Utiliza as APIs globais `window.wp`:
     - `wp.blocks.registerBlockType`
     - `wp.element.createElement`
     - `wp.blockEditor.RichText`
     - `wp.blockEditor.InspectorControls`
     - `wp.components.*` (`PanelBody`, `TextControl`, `RangeControl`, `SelectControl`, `ColorPalette`, `ToggleControl`, etc.)
   - Não requer compilação (Webpack/Babel/npm), funcionando de forma nativa e imediata no core do WordPress.

2. **Estrutura de Arquivos (Padrão Luiz0067)**:
   ```text
   luiz0067-topic-title-text/
   ├── luiz0067-topic-title-text.php  # Arquivo principal do plugin (registro e enfileiramento)
   ├── css/
   │   ├── style.css                 # Estilos frontend e editor (física, keyframes, temas)
   │   └── editor.css                # Overrides de tela de edição Gutenberg
   ├── js/
   │   ├── blocks/
   │   │   └── topic-title-text.js   # Definição e lógica do bloco Gutenberg (wp.*)
   │   └── frontend.js               # Interatividade do frontend (cópia de clipboard)
   ├── languages/                    # Internacionalização (pt_BR, en_US, es_ES, it_IT)
   │   ├── pt_BR.json
   │   ├── en_US.json
   │   ├── es_ES.json
   │   └── it_IT.json
   └── README.md
   ```

---

## Instalação

1. Clone ou copie o diretório `luiz0067-topic-title-text` para a pasta `/wp-content/plugins/` do seu WordPress.
2. Acesse o painel administrativo do WordPress > **Plugins** e ative o **Luiz0067 Antigravity Prompt / Floating Cards**.
3. No editor de posts ou páginas, clique no botão `+` para adicionar um novo bloco e procure por **"Antigravity Prompt / Floating Cards"** (ou use a categoria *Layout*).

---

## Atributos do Bloco

| Atributo | Tipo | Padrão | Descrição |
| :--- | :--- | :--- | :--- |
| `title` | string | `Estratégia de Prompt Antigravidade` | Título do tópico ou prompt |
| `content` | string | Texto demonstrativo | Conteúdo descritivo / texto do prompt |
| `tag` | string | `PROMPT #01` | Rótulo da badge superior |
| `speed` | number | `5` | Tempo em segundos de um ciclo completo de levitação |
| `delay` | number | `0` | Atraso em segundos antes de iniciar a flutuação |
| `color` | string | `#6366f1` | Cor de destaque em hexadecimal para badges e glow |
| `headingTag` | string | `h3` | Tag semântica HTML (`h2`, `h3`, `h4`, `h5`) |
| `cardStyle` | string | `glassmorphism` | Estilo: `glassmorphism`, `dark-neon`, `cyber-glow`, `minimal` |
| `actionType` | string | `copy` | Tipo de ação: `copy` (copiar texto), `link` (URL) ou `none` |
| `actionText` | string | `Copiar Prompt` | Rótulo exibido no botão |
| `actionUrl` | string | `""` | URL de destino quando `actionType` é `link` |
| `promptToCopy`| string | `""` | Prompt alternativo para cópia (fallback para `content`) |
| `showShadow` | boolean | `true` | Ativa/desativa a sombra de solo dinamicamente sincronizada |
| `alignment` | string | `center` | Alinhamento do card (`left`, `center`, `right`) |

---

## Licença

Distribuído sob a licença **GPL-2.0-or-later**.
