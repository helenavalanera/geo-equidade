# GEO-Equidade

Metodologia aberta de auditoria territorial em dados geoespaciais abertos.

Estudo-piloto aplicado a 12 bairros de Porto Alegre (RS), que compara a disponibilidade relativa de serviços mapeados no OpenStreetMap entre bairros centrais e não centrais, por meio do indicador **Razão Serviços/Nó**.

> O indicador não mede a oferta real de serviços, não estima a completude absoluta do OpenStreetMap e não estabelece relação causal com renda, raça/cor ou desempenho de sistemas públicos. Ele sinaliza territórios que devem passar por validação, atualização ou complementação de dados antes de alimentarem sistemas públicos de priorização, alerta, roteamento ou resposta a riscos.

## Problema público

Sistemas públicos de resposta a risco dependem cada vez mais de dados geoespaciais abertos. A abertura de uma base não garante, porém, que ela represente serviços e referências urbanas de modo equilibrado entre territórios. GEO-Equidade audita essa suposição antes que ela seja incorporada silenciosamente a decisões automatizadas.

## Metodologia

A descrição completa do método está no (notebooks/GEO_Equidade_Porto_Alegre.ipynb).

**Indicador central:**
Razão Serviços/Nó = feições classificadas como serviços / nós topológicos da rede de vias

## Fontes de dados

| Fonte | Uso no projeto | Catalogado em dados.gov.br |
|---|---|---|
| OpenStreetMap (extrato Geofabrik, ODbL) | Rede de vias e feições classificadas como serviços — insumo do indicador central | Não |
| IBGE/SIDRA | População por bairro, usada na seleção da amostra | Não |
| Malha geométrica dos municípios brasileiros (IBGE) | Delimitação e conferência do recorte municipal de Porto Alegre (código IBGE 4314902) | **Sim** — https://dados.gov.br/dados/conjuntos-dados/malha-geometrica-dos-municipios-brasileiros |

**Data de extração do extrato OSM:** não catalogada com carimbo de data/hora no momento da coleta original. O arquivo (`brazil-latest.osm.pbf`) foi obtido a partir da distribuição diária da Geofabrik. Pequenas variações numéricas observadas entre execuções decorrem dessa natureza dinâmica e da ausência de versionamento estrito do snapshot no piloto inicial.

## Como reproduzir

1. Clone o repositório e instale as dependências (`pip install -r requirements.txt`).
2. Baixe o extrato PBF do Brasil na Geofabrik e registre a data de download.
3. Execute o notebook em `notebooks/` na ordem apresentada.
4. Os resultados consolidados ficam em `data/resultados_piloto_porto_alegre.csv`; o dicionário de colunas está em `docs/dicionario_de_dados.md`.

## Limitações

Amostra intencional (N=12), não representativa estatisticamente. Macrozonas são classificação analítica própria, não regionalização oficial. Detalhes completos no notebook.

## Nota de reprodutibilidade e atualização temporal

O OpenStreetMap é uma base colaborativa e continuamente atualizada. Por esse motivo, reexecuções do pipeline com extratos obtidos em datas distintas podem produzir pequenas diferenças nas contagens de feições, ainda que utilizem os mesmos filtros e procedimentos.

Nesta execução, foram observadas pequenas diferenças nas contagens de serviços de 5 dos 12 bairros da amostra em relação a uma execução anterior deste mesmo pipeline — concentradas nos bairros centrais e de maior densidade (Centro Histórico, Santana, Menino-Deus, Jardim Leopoldina, Partenon). Os 7 bairros periféricos da amostra reproduziram exatamente os mesmos valores. Esse padrão é consistente com a hipótese de que áreas centrais recebem edição mais ativa da comunidade OpenStreetMap no intervalo entre extrações — mas essa hipótese não foi testada sistematicamente neste estudo, apenas observada nos dados desta execução.

A tabela e os gráficos deste repositório correspondem exclusivamente ao extrato e à execução aqui documentados.

## Licença

Código sob licença MIT (ver `LICENSE`). Dados do OpenStreetMap sob Open Database License (ODbL) — atribuição a OpenStreetMap e Geofabrik preservada em `data/README.md`.

## Autoria
Helena de Oliveira Valanera — 2026.
