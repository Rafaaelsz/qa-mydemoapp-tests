# My Demo App - Testes

Repositório de testes (manuais + automação com Maestro) em cima do app de prática da Sauce Labs
([my-demo-app-android](https://github.com/saucelabs/my-demo-app-android)).

Montei isso estudando pra uma vaga de QA, focando em Test Cases bem documentados e automação
com Maestro Studio.

## Estrutura

- `flows/` - os flows do Maestro (.yaml)
- `docs/testcases/` - documentação de cada test case

Cada test case tem o mesmo ID no doc e no flow, tipo `TC-001-login.md` e `TC-001-login-valido.yaml`,
pra ficar fácil achar a automação correspondente.

## Test cases

| ID | O que testa | Prioridade | Status |
|---|---|---|---|
| TC-001 | Login válido | Alta | não executado |
| TC-002 | Compra completa, do catálogo ao checkout | Alta | não executado |
| TC-003 | Ordenação de produtos | Média | não executado |
| TC-004 | Remover item do carrinho | Média | não executado |
| TC-005 | Reset do app (long press no header) | Média | não executado |
| TC-006 | QR Code Scanner + permissão de câmera | Baixa | não executado |

## Rodando os testes

Precisa do Maestro instalado:

```bash
curl -Ls "https://get.maestro.mobile.dev" | bash
```

E o app instalado num emulador Android rodando. Pra rodar um flow:

```bash
maestro test flows/login/TC-001-login-valido.yaml
```

Ou a pasta inteira:

```bash
maestro test flows/
```

## TODO

- automatizar TC-002 a TC-006
- ver se dá pra rodar isso no GitHub Actions
- adicionar casos de login inválido / usuário bloqueado