# bruno-poc

Template de testes de API com **[Bruno](https://www.usebruno.com/)** usando a API pública [ServeRest](https://serverest.dev).

Faz parte da organização [`qualidade-templates`](https://github.com/qualidade-templates).

## O que tem aqui

Collection versionada em arquivos `.bru`, com fluxo E2E:

1. Cadastrar usuário
2. Realizar login
3. Cadastrar produto
4. Cadastrar carrinho
5. Validar carrinho (E2E)

Cada request é responsável pelas próprias variáveis (`userId`, `token`, `produtoId`, `carrinhoId`). O E2E só orquestra via `bru.runRequest()`.

Também há um comparativo Bruno × Postman × Insomnia × Python em `docs/`.

## Estrutura

```
serverest/                 # collection Bruno
  usuarios/
  login/
  produtos/
  carrinhos/
  e2e/
  environments/Local.bru
docs/                      # comparativo em HTML/PDF
servrest-swagger.json      # OpenAPI do ServeRest (referência)
```

## Como usar

### Bruno Desktop

1. Instale o [Bruno](https://www.usebruno.com/downloads)
2. Abra a pasta `serverest/`
3. Selecione o environment **Local**
4. Execute `e2e / Fluxo E2E compra`

### Bruno CLI

```bash
cd serverest
npx @usebruno/cli run "e2e/Fluxo E2E compra.bru" --env Local
```

Gerar report HTML:

```bash
npx @usebruno/cli run "e2e/Fluxo E2E compra.bru" --env Local \
  --reporter-html reports/e2e-fluxo-compra.html
```

Gerar docs HTML da collection:

```bash
npx @usebruno/cli docs generate --all-envs --no-git-link \
  -o reports/serverest-documentation.html
```

## Environment

| Variável  | Valor padrão              |
|-----------|---------------------------|
| `baseUrl` | `https://serverest.dev`   |

## Repositórios relacionados

- [postman-poc](https://github.com/qualidade-templates/postman-poc) — mesmos fluxos no Postman

- [insomnia-poc](https://github.com/qualidade-templates/insomnia-poc) — mesmos fluxos no Insomnia
- [pactum-js-poc](https://github.com/qualidade-templates/pactum-js-poc) — mesmos fluxos em PactumJS + TypeScript
