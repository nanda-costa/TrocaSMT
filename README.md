# N4 · Troca de produto na linha SMT

Projeto final (Projeto 4) do módulo de Machine Learning — Curso de Capacitação Tecnológica em IA e Transformação Digital · UEA · Cyber Labs · EST.

**Equipe A** — Juliana Ballin Lima, Fernanda de Oliveira da Costa, Pedro Henrique Oliveira Dias.

## O problema

Na linha SMT, cada troca de produto para a linha: o operador tira os alimentadores do produto antigo, coloca os do novo, carrega o programa da máquina e confere a primeira placa. Enquanto isso a linha não produz, e a fábrica só tem ajuda extra para algumas trocas. O projeto usa informações já conhecidas **antes** da troca para apoiar essa decisão, respondendo duas perguntas sobre a mesma base de dados:

- **Regressão:** quantos minutos a troca vai levar (`tempo_troca_min`)?
- **Classificação:** a troca vai passar de 42 minutos (`troca_demorada`)?

## Estrutura do repositório

| Arquivo | Conteúdo |
|---|---|
| `N4_TrocaSMT_Aula04_Regressao.ipynb` | Preparo dos dados, método da média, árvore de regressão e regressão linear; escolha do modelo e avaliação no teste. |
| `N4_TrocaSMT_Aula06_Classificacao.ipynb` | Árvore de classificação, matriz de confusão, escolha da profundidade pela validação e avaliação no teste. |
| `resultados_N4/N4_regressao.json` | Métricas salvas da regressão (divisão dos dados, MAE por modelo, modelo escolhido, MAE no teste). |
| `resultados_N4/N4_classificacao.json` | Métricas salvas da classificação (tabela de profundidades, matriz de confusão e medidas de validação/teste). |
| `N4_limpo.csv` | Base de dados limpa usada pelos dois notebooks (~2.000 trocas, janeiro a agosto). |
| `N4_Apresentacao_EquipeA.html` | Slides da apresentação de 09/11 (abrir no navegador; setas do teclado navegam). |
| `N4_Enunciado_Trabalho_Final.pdf`, `N4_Enunciado_Regressao.pdf`, `M8_Projetos_Trabalho_Final.pdf`, `Template_Slides_Cyber_Labs.pdf` | Material de referência do curso. |

## Como rodar

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install pandas scikit-learn matplotlib jupyter
jupyter notebook
```

Abra os notebooks na ordem (regressão primeiro, depois classificação) e execute as células de cima para baixo. `N4_limpo.csv` já está na raiz do repositório, então a célula de leitura dos dados encontra o arquivo automaticamente.

## Resultados principais

**Regressão** — MAE (erro médio, em min) na validação: média de referência 6,10 · reta 3,02 · árvore (profundidade 4) 2,04. Modelo escolhido: árvore de profundidade 4. MAE no teste: **1,93 min** (meta da atividade: ≤ 3,5 min).

**Classificação** — árvore de profundidade 4, escolhida pelo menor total de erros na validação. No teste: VP 88, FN 13, FP 35, VN 273 — acurácia 88,3%, recall 87,1%, precisão 71,5%, F1 78,6%. O modelo erra mais por falso positivo (falso alarme) do que por falso negativo (troca demorada perdida).
