# Validação da entrega

Data: 05/11/2026, semestre 2026/2.

## Verificações executadas

- `npm ci --ignore-scripts --no-audit --no-fund`: dependências instaladas conforme o lockfile.
- `npm test`: 2 suítes e 22 testes aprovados.
- `npm run build`: compilação TypeScript aprovada.
- Collection Postman: JSON validado, com 12 requisições em sequência.

Os testes HTTP verificam cadastro, duplicidade, ordenação do histórico, cálculo de
indicadores, validação de corpo e URL, PUT completo, PATCH parcial, consulta por mês,
data de atualização, DELETE e retorno 404 após excluir. Também verificam isolamento
entre empresas e o efeito das alterações/exclusões sobre os indicadores.

## Limites da verificação

Os testes usam o repositório em memória. A execução da collection na aplicação Postman
e a integração real com o Firestore não foram realizadas. Para confirmar a persistência,
configure as credenciais conforme o README, execute a collection e reinicie a API.
Não foram realizados push ou alterações em um repositório remoto.

## Repetir localmente

```powershell
npm ci
npm test
npm run build
npm run start:dev
```

Importe `postman/monitoramento.postman_collection.json` e execute pelo Runner na ordem.
Cada execução gera uma empresa de teste exclusiva. Ao final, setembro é excluído;
o registro de outubro continua disponível (no Firestore ele permanece no banco).
