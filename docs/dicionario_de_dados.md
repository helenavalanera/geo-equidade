# Dicionário de dados — resultados_piloto_porto_alegre.csv

| Coluna | Tipo | Descrição |
|---|---|---|
| `Bairro` | texto | Nome do bairro de Porto Alegre |
| `Macrozona` | texto | Classificação analítica própria do estudo — Centro, Zona Norte, Zona Sul ou Zona Leste. Não é regionalização administrativa oficial |
| `População` | inteiro | População residente, IBGE/SIDRA |
| `Área (km²)` | decimal | Área do bairro obtida via geocodificação (Nominatim/OSM) e reprojeção para SIRGAS 2000 / UTM 22S (EPSG:31982) |
| `Densidade (hab/km²)` | decimal | População dividida pela área |
| `Critério Principal` | texto | Motivo de inclusão do bairro na amostra — "População" ou "Densidade" (top 10 em cada critério) |
| `Total de Nós (Vias)` | inteiro | Nós topológicos da rede de vias no OpenStreetMap (grau ≠ 2), extraídos do PBF via pyrosm |
| `Total de Serviços` | inteiro | Feições classificadas como serviços no OSM (`amenity`, `shop`, `healthcare`, `office`, `tourism`, `leisure`) |
| `Razão Serviços/Nó` | decimal | Indicador central — Total de Serviços dividido por Total de Nós (Vias) |

## Observações

- A amostra tem N=12 bairros, selecionados por recorte intencional (top população + top densidade, 3 por macrozona), não é representativa estatisticamente de todos os bairros de Porto Alegre.
- Bairros com falha de geocodificação ou processamento são registrados em tabela de auditoria separada, não preenchidos por estimativa.
- Nomes de coluna listados aqui refletem o pipeline após a correção de terminologia (`POI` → `Serviços`) e a inclusão da Zona Leste na seleção — confira se o CSV publicado já reflete essas mudanças antes de subir o repositório.
