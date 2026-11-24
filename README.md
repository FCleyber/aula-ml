# aula-ml: versionamento de dados e modelos com DVC

Prática de versionamento de dados, partições e modelos com Git e DVC, usando um classificador sintético de chamados (`comum` ou `urgente`).

## Pré-requisitos

- Git, Python 3.10 ou superior e DVC 3 (`pipx install 'dvc>=3,<4'`)
- Terminal Bash ou Zsh (no Windows, use o WSL)

## Armazenamento DVC

Os CSVs e o modelo ficam no remote `storage`, configurado em `.dvc/config` como a pasta irmã `../dvc-storage`. Para restaurar versões, o clone deve ficar ao lado de uma pasta `dvc-storage` que contenha os artefatos enviados com `dvc push`.

## Versões

| Tag | Conteúdo |
|---|---|
| `dados-v1` | Dataset inicial, com erro de anotação no ID 006 |
| `modelo-r1` | Modelo treinado com `chamados-v1` |
| `dados-v2` | Dataset com o rótulo do ID 006 corrigido |
| `modelo-r2` | Modelo treinado com `chamados-v2` |

## Restaurar uma versão

```bash
git clone <URL-DO-REPOSITORIO> aula-ml-restauracao
cd aula-ml-restauracao
git switch --detach modelo-r1
dvc pull
```

Depois, confira os hashes dos arquivos com os valores registrados em `reports/modelo.json`.

## Treinar

```bash
python3 src/train.py <id-do-modelo>
```

A comparação entre `r1` e `r2` está em `reports/comparacao.md`.
