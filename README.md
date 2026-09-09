# GEO-Equidade

Metodologia aberta de auditoria territorial em dados geoespaciais abertos.

Estudo-piloto aplicado a 12 bairros de Porto Alegre (RS), que compara a disponibilidade relativa de serviços mapeados no OpenStreetMap entre bairros centrais e não centrais, por meio do indicador **Razão Serviços/Nó**.

> O indicador não mede a oferta real de serviços, não estima a completude absoluta do OpenStreetMap e não estabelece relação causal com renda, raça/cor ou desempenho de sistemas públicos. Ele sinaliza territórios que devem passar por validação, atualização ou complementação de dados antes de alimentarem sistemas públicos de priorização, alerta, roteamento ou resposta a riscos.

Iniciativa submetida ao **2º Concurso de Reúso de Dados Abertos da CGU**.

## Problema público

Sistemas públicos de resposta a risco dependem cada vez mais de dados geoespaciais abertos. A abertura de uma base não garante, porém, que ela represente serviços e referências urbanas de modo equilibrado entre territórios. GEO-Equidade audita essa suposição antes que ela seja incorporada silenciosamente a decisões automatizadas.

## Metodologia

A descrição completa do método está no [notebook](notebooks/GEO_Equidade_Porto_Alegre.ipynb) e no artigo *"Quem não está no mapa, não está no algoritmo"* (referenciado abaixo). Este README não repete a metodologia — evita divergência entre versões.

**Indicador central:**

```
Razão Serviços/Nó = feições classificadas como serviços / nós topológicos da rede de vias
```

## Fontes de dados

| Fonte | Uso no projeto | Catalogado em dados.gov.br |
|---|---|---|
| OpenStreetMap (extrato Geofabrik, ODbL) | Rede de vias e feições classificadas como serviços — insumo do indicador central | Não |
| IBGE/SIDRA | População por bairro, usada na seleção da amostra | Não |
| Malha geométrica dos municípios brasileiros (IBGE) | Delimitação e conferência do recorte municipal de Porto Alegre (código IBGE 4314902) | **Sim** — https://dados.gov.br/dados/conjuntos-dados/malha-geometrica-dos-municipios-brasileiros |

## Como reproduzir

1. Clone o repositório e instale as dependências (`pip install -r requirements.txt`).
2. Baixe o extrato PBF do Brasil na Geofabrik e registre a data de download.
3. Execute o notebook em `notebooks/` na ordem apresentada.
4. Os resultados consolidados ficam em `data/resultados_piloto_porto_alegre.csv`; o dicionário de colunas está em `docs/dicionario_de_dados.md`.

## Limitações

Amostra intencional (N=12), não representativa estatisticamente. Macrozonas são classificação analítica própria, não regionalização oficial. Detalhes completos no notebook e no artigo.

## Licença

Código sob licença MIT (ver `LICENSE`). Dados do OpenStreetMap sob Open Database License (ODbL) — atribuição a OpenStreetMap e Geofabrik preservada em `data/README.md`.

## Autoria

Helena de Oliveira Valanera — 2026.
