---
# AGENTS.md — developer-docs (Mintlify)

Instruções para agentes e autores que escrevem documentação neste repositório.

## Sobre o projeto

- Site Mintlify (`docs.json` + páginas MDX)
- Idioma: **pt-BR**
- Títulos em **sentence case**
- Frontmatter mínimo: `title`, `sidebarTitle`, `description`
- Componentes Mintlify quando úteis: `Steps`, `Note`, `Warning`, `Tip`, `Card`, `CardGroup`, `CodeGroup`

## Escopo Fiscal SDK (CT-e)

### API pública (obrigatório)

Documente **somente**:

1. `$cte->…->handle()` — client `Suot\Fiscal\Cte\Application\Cte`
2. `*Command::create()…->build()` / `*Query::create()…->build()` + `Handler::handle()` ou `$cte->handle($cmd)`

### Nunca documentar como API do consumidor

- `CTeBuilder`, `EmitirCTe*`, `AutorizarNFe*`, `AutorizarCte*`
- `Operation/*` como entry point (`*Input`, `*::execute()`, `*Service`)
- `*InputMapper`, `IssueCteCommandBuilder`, `IssueCteCommandParts`
- `CteClient` como porta principal

### Namespaces

- Application: `Suot\Fiscal\Cte\Application\…`
- Data / VO CT-e: `Suot\Fiscal\Cte\Data\…`, `Suot\Fiscal\Cte\ValueObject\…`
- Core VO: `Suot\Fiscal\Core\ValueObject\…`
- Results: `Suot\Fiscal\Cte\Operation\…\*Result` (retorno público; pasta `Operation` de **serviços** continua interna)

### Pacotes Composer

Use `usesuot/fiscal-core`, `usesuot/fiscal-sefaz`, `usesuot/fiscal-cte`, `usesuot/fiscal-laravel` — não `suot/fiscal-*` inventado.

### Licença e prontidão

- Ler docs **não** exige licença; `composer require` no registry **exige**
- Não declare production-ready sem caveat (schemas, fixtures, ciclo de vida, homologação)
- Vencimento de update ≠ kill switch no runtime instalado

### Página de capacidade (padrão)

1. O quê / quando  
2. Exemplo fluent  
3. Equivalente Command/Query (breve)  
4. Como ler o Result  
5. Link para `examples/cte/…` ou `bin/dx/…`

### Fonte de verdade do código

Antes de inventar método ou parâmetro, leia o código em `../fiscal-sdk-php/packages/cte/src/Application/` e os exemplos em `examples/cte/` / `bin/dx/`.

## Estilo

- Ativo, 2ª pessoa, frases curtas
- Precisão de código > marketing
- Signal (`#FB0927`) é marca, não cor de erro — na docs, use `Warning`/`Tip` sem metáfora de cor
- Sem emoji

## Navegação

Ao criar páginas novas, atualize `docs.json`. Remova stubs órfãos (ex.: `fiscal/cte.mdx` se existir `fiscal/cte/index.mdx`).
