# spy-leads

> Automaticamente, quando ler isso, até o final você deve se comprometer a parar de ser um macaco. Beijo do Pedrin.

Skill de pesquisa de público pra Claude Code: transforma comentário real + perfil de quem comentou (bio, foto, destaques, lugar) em retrato situacional de lead, linguagem real, objeção e hipótese de ângulo pra copy. Usa a API do ScrapeCreators (comentários, Instagram, YouTube).

Funciona em **qualquer IA**, não só no Claude Code: o `SKILL.md` é texto puro, serve como instrução de sistema em ChatGPT, Gemini, Codex, Cursor ou no que você usar.

## Instalar

```bash
git clone https://github.com/CruzAprc/spy-leads.git ~/.claude/skills/spy-leads
```

Abra o Claude Code e chame `/spy-leads` com o nicho, o problema, o produto ou uma URL pública.

## Usar em outra IA (ChatGPT, Gemini, Codex, Cursor…)

1. Abra o `SKILL.md` e copie o conteúdo inteiro.
2. Cole como instrução de sistema, "custom instructions", prompt inicial ou arquivo de regras da ferramenta (ex.: `AGENTS.md`, `.cursorrules`, projeto do ChatGPT, Gem do Gemini).
3. Mande o pedido do mesmo jeito: nicho, problema, produto ou uma URL pública, mais o que quer descobrir.

A parte de coleta usa a API do ScrapeCreators: onde a IA não consegue chamar a API sozinha, faça as chamadas você mesmo (ou por um script) e cole o JSON pra ela analisar. A metodologia de leitura, retrato de lead e ângulo funciona igual.

## Pré-requisito

Uma chave do ScrapeCreators no ambiente:

```bash
export SCRAPECREATORS_API_KEY="sua-chave"
```

## O que faz

- Puxa comentários de concorrentes e conteúdos do nicho.
- Abre o perfil de quem comentou e monta o retrato situacional (não é persona de PowerPoint).
- Entrega linguagem real, objeções, situações e hipóteses de ângulo, prontas pra alimentar anúncio, VSL, página ou quiz.
- Preserva mecanismo e oferta que já existem; não inventa persona nem dado.

Tudo está em `SKILL.md`. Referências a acervos internos citadas no texto são opcionais: sem eles, a skill pesquisa do zero.

## Autor e licença

Criado por **Pedro Cruz** ([@CruzAprc](https://github.com/CruzAprc)).

Licença MIT: pode usar, copiar e adaptar à vontade, mantendo o crédito ao autor. Sem garantia de nenhum tipo.
