# Google Ads Ratos

Skill de execucao para Google Ads no ecossistema Ratos. Usa o SDK oficial `google-ads` do Python com queries GAQL.

## Instalacao

```bash
pip3 install google-ads protobuf
```

## Configuracao

Crie o arquivo `~/.claude/skills/google-ads-ratos/.env` com:

```
GOOGLE_ADS_DEVELOPER_TOKEN="seu-developer-token"
GOOGLE_ADS_CLIENT_ID="seu-client-id.apps.googleusercontent.com"
GOOGLE_ADS_CLIENT_SECRET="seu-client-secret"
GOOGLE_ADS_REFRESH_TOKEN="seu-refresh-token"
GOOGLE_ADS_LOGIN_CUSTOMER_ID="1234567890"
```

Ou use o formato padrao `google-ads.yaml` na mesma pasta.

## Scripts

| Script | Funcao |
|--------|--------|
| `read.py` | Leitura de campanhas, ad groups, keywords, ads, search terms |
| `insights.py` | Metricas e breakdowns (account, campaign, daily, device, hourly) |
| `create.py` | Criar campanhas, ad groups, keywords, RSAs, extensoes |
| `update.py` | Editar status, orcamento, bids |
| `delete.py` | Remover keywords, negativas, ads |

## Uso

```bash
cd ~/.claude/skills/google-ads-ratos/scripts

# Listar contas
python3 read.py accounts

# Campanhas de uma conta
python3 read.py campaigns --customer-id 1234567890

# Insights dos ultimos 30 dias
python3 insights.py account --customer-id 1234567890 --date-range LAST_30_DAYS

# Criar campanha (sempre PAUSED)
python3 create.py campaign --customer-id 1234567890 --name "Search-Leads" --type SEARCH --budget 5000
```

## Estrutura

```
google-ads-ratos/
├── SKILL.md              # Orquestrador (instrucoes pro Claude)
├── README.md             # Esta documentacao
├── contas.yaml           # Cadastro de contas/clientes
├── .gitignore
├── references/
│   └── api-reference.md  # Referencia de GAQL queries uteis
└── scripts/
    ├── lib/
    │   └── __init__.py   # Auth, .env loader, helpers
    ├── read.py           # Leitura
    ├── insights.py       # Metricas e breakdowns
    ├── create.py         # Criacao
    ├── update.py         # Edicao
    └── delete.py         # Exclusao
```
