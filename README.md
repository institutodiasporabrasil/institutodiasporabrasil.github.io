# Dados — Instituto Diáspora Brasil

Página-hub com as áreas e menus dos painéis de dados do Instituto. Cada painel vive no
seu próprio repositório da organização `institutodiasporabrasil` (ex.: `brasileiros-eua`)
e é carregado aqui por iframe com `?embed=1`.

Publicado como GitHub Pages da organização: https://institutodiasporabrasil.github.io/

## Lista do menu: `menu.csv`

Regiões, países, estados/províncias, cidades e os conteúdos de cada um ficam no arquivo
`menu.csv`, separado por ponto e vírgula (abre direto no Excel).

| coluna | o que vai nela |
|---|---|
| `tipo` | `mundo`, `regiao`, `pais`, `estado` ou `cidade` |
| `nome` | nome curto: `Estados Unidos`, `Flórida`, `Boston` |
| `titulo_no_menu` | como aparece no menu: `Brasileiros nos Estados Unidos` (vazio = usa o nome) |
| `regiao` | só para país: o nome da região, igual ao da linha da região |
| `pais` | para estado e cidade: o nome do país, igual ao da linha do país |
| `estado` | só para cidade: o nome do estado/província (pode ficar vazio) |
| `conteudos` | para mundo, região e país: separados por ` \| `; o 1º abre por padrão (vazio = `População Total`) |

Exemplos:

```
estado;Ontário;Brasileiros em Ontário;;Canadá;;
cidade;Miami;Miami;;Estados Unidos;Flórida;
```

Cuidados:
- A ordem das linhas é a ordem no menu.
- O país, a região ou o estado citado precisa existir no arquivo com o mesmo nome (acentos contam).
- Trocar o `nome` de um item muda o identificador dele; se o item já tiver painel ligado,
  é preciso atualizar também o `DASHBOARDS` em `index.html`.
- No Excel, salvar como **CSV UTF-8 (delimitado por vírgulas)** para não perder os acentos.
- Depois de publicar, abra https://institutodiasporabrasil.github.io/?verificar — a página
  mostra no topo se alguma linha tem problema (linhas com erro são ignoradas, o resto do menu continua).

## Ligar um painel a um item do menu

Acrescente-o ao objeto `DASHBOARDS` em `index.html` (chave `<nível>:<id>|<conteúdo>`,
valor = caminho `/<repositório>/`). O `id` é o nome sem acentos, em minúsculas e com hífens
(`Estados Unidos` → `estados-unidos`). Itens sem painel mostram "EM BREVE".

## No site WordPress

Dentro de um iframe (ou com `?embed=1`) o hub entra no modo aplicativo: o topo fica fixo e só o
painel rola. Código para o bloco HTML do Elementor (ajustar `72px` à altura do cabeçalho do site):

```html
<div class="idb-dados">
  <iframe src="https://institutodiasporabrasil.github.io/?embed=1"
          title="Painéis de dados — Instituto Diáspora Brasil"
          loading="lazy" allow="fullscreen"></iframe>
</div>
<style>
  .idb-dados iframe { display:block; width:100%; border:0;
    height: calc(100vh - 72px); height: calc(100dvh - 72px); }
</style>
```
