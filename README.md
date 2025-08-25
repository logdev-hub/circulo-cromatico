# 🎨 Círculo Cromático HSL — Avançado (PRO)

> Ferramenta web autônoma para criação, inspeção e exportação de paletas de cores baseada em HSL — com recursos avançados: Bootstrap Toasts, Undo simples, checagem WCAG, Eyedropper (importar imagem) e múltiplos formatos de exportação (CSS / JSON / PNG / SCSS / Tailwind / Tokens / ASE-like / CMYK). 🧰

---

## 📌 Visão geral

Este projeto é um **arquivo HTML autônomo** (sem necessidade de servidor) que permite explorar o espaço de cores HSL, criar paletas harmônicas, validar acessibilidade (WCAG), extrair cores de imagens e exportar as paletas em vários formatos prontos para uso em design e desenvolvimento.

Arquivo principal: `Circulo-cromatico-hsl-avancado-pro-cmyk.html`

---

## ✨ Funcionalidades principais

- 🔵 Disco cromático interativo (matiz × saturação) — clique ou arraste para selecionar cores.  
- 🎛️ Controles H / S / L e número de cores (2–8).  
- ↩️ **Undo** simples (pilha limitada) para desfazer mudanças.  
- 🟢 **Bootstrap Toasts** para notificações elegantes.  
- ♿ Checagem **WCAG** (contrast ratio) com sugestão automática de cor acessível quando necessário.  
- 🖼️ **Eyedropper / Importar imagem**: carregue uma imagem e clique para extrair cores.  
- 📦 Exportações: CSS variables, JSON, PNG (imagem da paleta), SCSS, Tailwind snippet, Tokens JSON, ASE-like (JSON) e **CMYK (CSV + JSON)**.  
- 🔁 Marker (bolinha) posicionado corretamente no disco mesmo após redimensionamento.

---

## 🚀 Como abrir / executar localmente

1. Baixe `Circulo-cromatico-hsl-avancado-pro-cmyk.html` e o `README.md` (este arquivo).  
2. Abra o arquivo HTML no navegador moderno (Chrome, Firefox, Edge, Safari).  
3. Recomendações: ter conexão para carregar Bootstrap via CDN ou substituir por assets locais.

---

## 🧭 Instruções rápidas de uso

1. **Selecionar cor**: clique/arraste no disco para ajustar Hue e Saturation. Ajuste Lightness com o slider.  
2. **Gerar paleta**: escolha uma relação harmônica e a quantidade de cores; a paleta será mostrada.  
3. **Copiar cor**: clique em qualquer swatch para copiar o HEX para a área de transferência.  
4. **Undo**: clique em `Undo` para desfazer a última ação (até 30 passos por padrão).  
5. **Importar imagem**: carregue uma imagem, ative o Eyedropper e clique na imagem para aplicar a cor selecionada.  
6. **WCAG**: painel lateral mostra contraste (AA / AAA). Se uma cor falhar, use `Sugerir cor acessível` para ajustar automaticamente.  
7. **Exportar**: use os botões para gerar CSS / JSON / PNG / SCSS / Tailwind / Tokens / ASE-like / CMYK.

---

## 📁 Formatos de exportação

- **Variáveis CSS** — bloco `:root { --color-1: #xxxxxx; ... }`  
- **JSON** — `palette.json` com objetos `{ hex, h, s, l }`  
- **PNG** — imagem horizontal com os swatches e seus HEX  
- **SCSS** — variáveis SCSS copiadas para a área de transferência  
- **Tailwind** — snippet `tailwind.config.js` para `extend.colors`  
- **Tokens JSON** — `tokens.json` pronto para design systems  
- **ASE-like (JSON)** — estrutura JSON similar a um arquivo ASE para integração futura  
- **CMYK (CSV)** — `palette-cmyk.csv` com colunas `color_hex,c_percent,m_percent,y_percent,k_percent` e JSON CMYK copiado para clipboard

> Exemplo CSV (linha):  
> `#2ad54f,22,0,62,0` → HEX `#2ad54f` → C=22% M=0% Y=62% K=0%

---

## 🖨️ Sobre a conversão CMYK

- A conversão implementada segue a **fórmula matemática padrão** (HEX → RGB → CMYK) e é adequada para estimativas e comunicação entre designers / desenvolvedores.  
- **Aviso importante**: CMYK é dependente de **perfil ICC** (por exemplo: FOGRA39, SWOP). Para impressão profissional com fidelidade de cor, converta em um software que suporte ICC ou use um script que aplique um perfil ICC específico. Posso ajudar a criar um script Node.js para isso se necessário. 🔧

---

## ♿ Acessibilidade (WCAG)

- Cálculo de contraste usando a fórmula recomendada pelo WCAG.  
- Indicadores de `AA` (≥ 4.5) e `AAA` (≥ 7.0) para cada par (base → cor).  
- Botão de **Sugerir cor acessível** que ajusta a luminosidade da cor alvo até atingir o contraste mínimo com a cor base (tentativa automática).

---

## 🧩 Estrutura do código (pontos chave)

- `drawWheel()` — desenha o círculo cromático.  
- `clientToHS()` — converte clique/coords para H / S.  
- `syncFromState()` — atualiza UI e posiciona marker corretamente.  
- `generatePalette()` — gera paleta segundo a harmonia selecionada.  
- `hslToHex()`, `hslToRgb()`, `hexToRgb()` — utilitários de cor.  
- `contrastRatio()` / `suggestAccessible()` — WCAG checks & suggestions.  
- `hexToCmyk()` / `exportCMYK()` — conversão e export para CMYK.  
- Eyedropper: `imageCanvas` + leitura de pixel via `getImageData`.  
- Undo: `undoStack` + `pushUndo()` — histórico limitado.

---

## 🛠️ Extensões & melhorias futuras

- ✅ LocalStorage para salvar paletas e presets.  
- ✅ Compartilhamento via URL codificada (paleta na query string).  
- 🔁 Undo/Redo avançado (mais granular).  
- 🖨️ Export CMYK com perfis ICC via Node.js (para gráficas profissionais).  
- 🔗 Plugin / integração com Figma ou CLI para enviar paletas diretamente.  
- 🧪 Simulador de daltonismo (protanopia / deuteranopia / tritanopia).  
- 📦 Export formatos nativos (`.ase`, `.aco`) com suporte a metadados.

---

## 📋 Licença

MIT — sinta-se livre para usar, modificar e distribuir.

---

## ✉️ Contato / Próximos passos

Se quiser, eu posso já implementar para você:

- ✅ LocalStorage + salvar paletas  
- ✅ Export CMYK com perfil ICC (Node.js)  
- ✅ Gerar arquivos `.ase` / `.aco` reais

Responda com qual opção prefere e eu preparo os arquivos / scripts correspondentes. 🚀

---

*README gerado automaticamente com emojis — pronto para download.*  
