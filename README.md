# Mintlify Starter Kit

Click on `Use this template` to copy the Mintlify starter kit. The starter kit contains examples including

- Guide pages
- Navigation
- Customizations
- API Reference pages
- Use of popular components

### Development

Install the [Mintlify CLI](https://www.npmjs.com/package/mintlify) to preview the documentation changes locally. To install, use the following command

```
npm i -g mintlify
```

Run the following command at the root of your documentation (where docs.json is)

```
mintlify dev
```

### Publishing Changes

Install our Github App to auto propagate changes from your repo to your deployment. Changes will be deployed to production automatically after pushing to the default branch. Find the link to install on your dashboard. 

#### Troubleshooting

- Mintlify dev isn't running - Run `mintlify install` it'll re-install dependencies.
- Page loads as a 404 - Make sure you are running in a folder with `docs.json`

## Entrada de changelog

Toda versão do manager publicada em produção com mudança de contrato (rota, evento, campo, código
de erro ou comportamento observável) ganha uma entrada em `changelog.mdx` e em `en/changelog.mdx`,
no mesmo dia da publicação.

### Formato

- Um bloco `<Update>` por versão, no topo do arquivo, com `label` (mês e ano), `description`
  (uma frase) e `tags`.
- Seções na ordem: o que mudou, em uma ou duas frases; `## Rotas novas`; `## Rotas alteradas`;
  `## Eventos`; `## Campos novos`; `## Códigos de erro`. Use só as seções que se aplicam.
- Cada rota, evento e campo é um item de lista com link para a seção da documentação que o
  descreve. Âncoras sem acento (`#sincronizacao-de-templates`).
- Mudança que exige ação do integrador ganha a seção `## Atenção`, com a nota de migração: o que
  muda, a partir de quando e o que fazer.
- Versão sem mudança de contrato ganha a entrada sem lista: uma frase que diz o que mudou para o
  integrador.
- As duas línguas têm a mesma estrutura: pt-BR na raiz, inglês em `en/`.

### Antes de publicar

1. Rode `npx mint validate` e `npx mint broken-links`.
2. Rode a verificação de termos nas linhas alteradas. O texto descreve só o comportamento em
   produção: sem "ainda", "por enquanto", "em breve", "homologação", "validado", "confirmar",
   nomes de variável de ambiente, nomes de tabela ou de fila, nem identificadores de tarefa ou de
   spec.

   ```sh
   git diff -U0 -- '*.mdx' | grep '^+' | grep -n -i -E 'ainda|por enquanto|em breve|homologa|validad|confirmar|[A-Z]+_[A-Z_]+='
   ```

3. Regenere `api-reference/openapi.json` a partir do manager quando a versão muda rotas.
