# Comparação entre os modelos r1 e r2

## Alteração feita

O rótulo do chamado `006` ("bloqueio de acesso") foi corrigido de `comum` para `urgente`, gerando o dataset `chamados-v2`. A partição treino/teste (`split.csv`) não foi alterada.

## Métricas (mesma partição de teste, 4 exemplos)

| Métrica | r1 | r2 |
|---|---|---|
| Acurácia | 0.75 (3/4) | 1.0 (4/4) |
| Recall de `urgente` | 0.5 (1/2) | 1.0 (2/2) |
| Recall de `comum` | 1.0 (2/2) | 1.0 (2/2) |

## Hashes

| Item | r1 | r2 |
|---|---|---|
| `split_sha256` | `2ef820171c1a4625fe216e6da67c7c8dcf9d97a08288c0239cd23f1a6961d981` | igual a r1 |
| `dataset_sha256` | `bc3fd86a3a5f598841a58839a9726d901fa7e8361ffe79c5b43873ad8a1328ac` | `4ca2e29cb930a9161c2a851b3c71f5529dbb812db607ee4a5ea95d2223baa14d` |
| `artifact_sha256` | `09d965544c9298c5586af0a1becbf07fb3f3c7b7c228a803ab91179f8b458a09` | `3bcddff15fe272fe16e092dfb76dab30fa3786cd8c2ce4849ccf5ace002c6ee6` |

## Evidência de restauração do r1 (clone limpo)

Commit `fa93e5d917b10e2ed1cf4efdf15d56256acb7cdc` (tag `modelo-r1`). Após `dvc pull`, os hashes conferiram com o manifesto:

- `data/chamados.csv`: `bc3fd86a3a5f598841a58839a9726d901fa7e8361ffe79c5b43873ad8a1328ac`
- `data/split.csv`: `2ef820171c1a4625fe216e6da67c7c8dcf9d97a08288c0239cd23f1a6961d981`
- `models/model.json`: `09d965544c9298c5586af0a1becbf07fb3f3c7b7c228a803ab91179f8b458a09`

## Decisão

**Aceitar r2 para este exercício.** O critério era melhorar o recall de urgentes sem reduzir o de comuns, com a mesma partição de teste. O recall de urgentes subiu de 0.5 para 1.0 e o de comuns se manteve em 1.0.

Ressalva: o conjunto de teste tem apenas 4 exemplos, então a comparação demonstra o efeito da correção neste exercício, mas não permite conclusões estatísticas.
