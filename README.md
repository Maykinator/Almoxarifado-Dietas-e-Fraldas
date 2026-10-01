# Almoxarifado — Dietas e Fraldas

Sistema de controle de almoxarifado para conferência, armazenamento e entrega de dietas, suplementos e fraldas a beneficiários. Roda inteiro num único arquivo HTML, sem instalação, sem servidor e sem build — abre direto no navegador, no computador ou no celular.

Feito por **Maykel**.

## Funcionalidades

- **Localizar** — busca por número ou nome e mostra, pra cada beneficiário, onde cada categoria (dieta/fralda) está guardada e quantos volumes já chegaram.
- **Conferir** — recebimento dos volumes: confere item a item, ajusta quantidade recebida, define o local no almoxarifado e marca divergências. Leitura de etiqueta por QR (foto ou câmera).
- **Entregar** — lista quem está pronto pra retirada e registra a entrega (volumes retirados + quem levou).
- **Dados** — importa a planilha do mês (.xlsx/.csv, com detecção automática de colunas), exporta Excel formatado para impressão/conferência, gera etiquetas com QR, gerencia locais e competências (meses).
- **Painel** — indicadores do mês, pacotes incompletos, volumes sem local, movimentação do dia (entradas e saídas, incluindo registros avulsos) e exportação do relatório diário.
- Identidade de beneficiário por **número + nome**: números repetidos para pessoas diferentes não se confundem; mesma pessoa com o mesmo número nunca duplica.

## Como usar

Existem duas formas de rodar o sistema, dependendo de onde este repositório for aberto:

**1. Local (este repositório / GitHub Pages / baixado no PC)**
Basta abrir o `index.html` num navegador. Os dados ficam salvos no armazenamento local *daquele navegador* — ótimo para um computador fixo do almoxarifado, mas não sincroniza entre aparelhos. Útil quando não há acesso ao link publicado ou quando qualquer pessoa da equipe precisa só abrir o arquivo e usar.

**2. Publicado (com sincronização entre celular e computador)**
A versão publicada via Claude roda com banco de dados compartilhado — qualquer aparelho que abrir o link vê os mesmos dados em tempo real, e ganha de brinde a leitura de etiqueta por IA (foto da etiqueta sem QR, planilha impressa por foto). Essa parte depende da plataforma onde foi publicado e não funciona rodando o arquivo sozinho.

## Formato da planilha de importação

O importador tenta detectar as colunas sozinho a partir do cabeçalho (aceita variações como "Nº", "Nome", "Item", "Marca", "Tamanho", "Tipo", "Quantidade/Mês" etc.) e deixa confirmar/corrigir antes de importar. Linhas de continuação (mesmo beneficiário, item extra) não precisam repetir número e nome. Linhas de título ou cabeçalho repetido no meio da planilha são identificadas e ignoradas automaticamente.

## Tecnologias

HTML/CSS/JavaScript puro, sem framework e sem passo de build. Bibliotecas carregadas via CDN:

- [SheetJS (xlsx-js-style)](https://github.com/gitbrent/xlsx-js-style) — leitura e escrita de planilhas Excel com formatação.
- [qrcodejs](https://github.com/davidshimjs/qrcodejs) — geração de QR code para etiquetas.
- [html5-qrcode](https://github.com/mebjas/html5-qrcode) — leitura de QR code por foto ou câmera.

## Limitações

- Rodando localmente (fora da versão publicada), os dados ficam só no navegador usado — vale exportar backup em Excel com frequência.
- A leitura de etiqueta por IA (sem QR) e a leitura de planilha impressa por foto só funcionam na versão publicada.
- Requer internet ao carregar a página (para baixar as bibliotecas); depois disso funciona offline.
