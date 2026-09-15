# spy-leads

Skill de pesquisa de público pra Claude Code: transforma comentário real + perfil de quem comentou (bio, foto, destaques, lugar) em retrato situacional de lead, linguagem real, objeção e hipótese de ângulo pra copy. Usa a API do ScrapeCreators (comentários, Instagram, YouTube).

## Instalar

```bash
git clone https://github.com/CruzAprc/spy-leads.git ~/.claude/skills/spy-leads
```

Abra o Claude Code e chame `/spy-leads` com o nicho, o problema, o produto ou uma URL pública.

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

## Licença

MIT.
