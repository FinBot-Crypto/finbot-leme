# finbot-leme

Projeto independente da estratégia Leme.

Inclui seleção de universo, engine de decisão, guardian, shadow e os processos offline de treinamento/validação dos modelos do Leme. O Leme publica ordens; a execução pertence exclusivamente ao `finbot-core`.

## Contrato

- entrada: `market.universe.v1`;
- compatibilidade de entrada legada: `leme.universe` durante a migração;
- saída: `trade.order.v1`;
- eventos de fechamento consumidos: `trade.closed.v1`.

## Deploy

O `.env` é exclusivo do Leme. Ele não deve conter as chaves privadas usadas pelo Core. O banco usa um usuário próprio com permissões limitadas ao funcionamento da estratégia.

```bash
docker compose --env-file .env up -d --build
```

Os serviços de ML offline ficam no profile `offline` e não interrompem o runtime da estratégia:

```bash
docker compose --env-file .env --profile offline up -d --build fb-ml-training fb-ml-validation
```
