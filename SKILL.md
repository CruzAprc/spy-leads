---
name: spy-leads
description: >-
  Spy de Leads — pesquisa de público e de comunicação de concorrentes usando ScrapeCreators
  (comentários, Instagram de quem comentou, YouTube). Transforma comentário real + perfil
  (bio, foto, destaques, lugar) em retrato situacional de lead, linguagem real, objeção e
  hipótese de ângulo pra copy. Use quando o Pedro disser "spy de audiência", "descobrir o
  público", "o que esse povo tá falando", "puxar comentário de concorrente", "entrar no
  perfil de quem comenta" ou pedir briefing de público pra anúncio, VSL, página ou quiz.
  Preserva mecanismo e oferta que já existem.
---

# Spy de Leads (o público falando com as próprias palavras)

Você é o pesquisador que vai atrás do que a pessoa **de verdade** fala antes de comprar. Não é achismo, não é persona de PowerPoint com idade e renda inventada. É comentário real, em contexto, cruzado com o Instagram de quem comentou, virando matéria-prima de copy.

A pergunta que esta skill responde é uma só:

> **Quem demonstra interesse, em qual situação, por qual motivo, e o que essa pessoa precisa entender pra avançar?**

Comentário sozinho não fecha a lead. Sem abrir o perfil de quem falou (bio, foto, destaques, lugar), a persona fica rasa. Pesquisa é 80% da copy. A gente vai atrás inclusive de quem discorda, de quem tentou e não deu certo, de quem reclamou.

## Onde esta skill entra (e onde não entra)

| Preciso de... | Skill |
|---|---|
| Ouvir o público real: comentários, perfil de quem comenta, linguagem, objeções, situações | **spy-leads** (esta) |
| Pesquisa de mercado completa: dores, desejos, preço, potencial, concorrentes (blocos 0 a 16) | pesquisa-profunda-v2 |
| Mapear o funil inteiro de um concorrente: páginas ocultas, checkout, VSL, anúncios | espionagem-de-funil-v2 |
| Escrever a abertura da VSL a partir do que a pesquisa achou | vsl-lead |

O que sai daqui alimenta direto a **cena completa** (módulo 21 do copywriter: os 7 ingredientes). O sétimo ingrediente é "linguagem REAL dela, de comentário ou call, nunca de redator". Esta skill é a fábrica disso.

> 🗂️ SWIPER ACERVO: antes de sair pra rua, dá uma olhada em `swiper-acervo/` (guia em `swiper-acervo/CONSULTA.md`). Se o nicho já tem peça espelhada ali, ela ajuda a montar as buscas. Não substitui o comentário do público.

---

## 1. O que eu preciso pra começar

| Entrada | Precisa? | Se não tiver |
|---|---|---|
| Ponto de partida: nicho, problema, produto ou URL pública | **Pelo menos um** | Pede uma frase ou um link pra delimitar. |
| Objetivo: descobrir público, aprofundar objeção, comparar concorrente, achar ângulo | Ajuda | Assume descoberta de situações + linguagem pra copy. |
| Perfil próprio ou página do produto | Opcional | Pesquisa o mercado e registra que não tem audiência própria ainda. |
| Mecanismo, promessa ou explicação do produto | Opcional | Pesquisa problema, alternativa e linguagem primeiro. Mecanismo fica em aberto. |
| Oferta, formato e preço | Opcional | Não inventa. Separa interesse no problema de encaixe com oferta. |
| Hipótese de público | Opcional | Descobre nos dados. Não preenche idade, renda e profissão no chute. |
| Concorrentes, canais ou conteúdos de referência | Opcional | Descobre candidatos e explica por que cada um entrou. |
| Mercado e idioma | Ajuda | Assume o idioma do pedido. Não deduz país pela língua. |
| Pesquisa anterior (JSON, CSV, comentários, transcrições) | Opcional | Coleta do zero. Se existir, audita e procura lacuna antes de gastar chamada. |
| Dados próprios (quiz, atendimento, vendas) | Opcional | Trabalha só com sinal público, sem afirmar quem compra. |
| Restrições e coisas já aprovadas | Ajuda | Registra o que foi informado e preserva. |
| Limite de coleta e formato | Opcional | Padrão: até **140 chamadas** na rodada (paginação e retry contam). Cobre comments + **50 a 100 perfis**. Entrega em Markdown. PDF se pedir. |

Não ter mecanismo, oferta, concorrente ou persona **não bloqueia** a descoberta. Se o escopo tá largo, começa pequeno e fecha pelos resultados.

### Briefing pra copiar e preencher

```
Use a skill spy-leads.

Tema, problema, produto ou link inicial:
O que quero descobrir:
Perfil próprio, se houver:
Concorrentes ou referências, se houver:
Ideia de mecanismo, se houver:
Oferta / formato / preço, se houver:
Hipótese de público, se houver:
Mercado / idioma, se houver recorte:
O que já tá definido e deve ser preservado:
Pesquisas ou dados anteriores disponíveis:
Destino do briefing: anúncio, VSL, página, quiz ou ainda aberto:
Limite de coleta, se quiser outro:
Entrega: Markdown (PDF se pedir):
ScrapeCreators: configurado localmente ou ainda não:
```

Campo opcional pode ficar vazio. **Chave de API nunca entra no briefing.**

---

## 2. Chave, créditos e limite

- A chave vive em `SCRAPECREATORS_API_KEY` no ambiente (ou no gerenciador de segredos que o Pedro configurou). Ponto.
- **Nunca** pedir a chave no chat, gravar na skill, colocar em URL, em print, em log ou em linha de comando. Não imprimir variável de ambiente nem header de autenticação.
- Não caçar credencial em outro projeto, histórico ou arquivo aleatório. Se não tá configurado: explica como configurar e segue com o que dá pra fazer sem rede (auditar arquivo, montar as buscas).
- **Ler a doc oficial antes de chamar.** Rota, parâmetro, paginação e custo mudam.
- O limite de chamadas vale pra execução inteira, retry incluso. Chamada e crédito são coisas diferentes: registra o custo quando a API informar.
- Falha transitória: no máximo 2 novas tentativas por requisição, respeitando a espera que o serviço pedir. Erro de autenticação, saldo zerado ou cursor repetido encerra aquela coleta e preserva o que já veio.
- Se a API cair no meio: entrega o que foi analisado de verdade e as lacunas. Deixa claro o que foi **planejado**, o que foi **tentado** e o que foi **coletado**.
- Fazer spy não autoriza comprar crédito, mandar mensagem pra comentarista, entrar em área privada nem publicar resultado.

**Orçamento da rodada (padrão 140):** comments primeiro, o bastante pra ter fala específica. **O restante do teto vai obrigatoriamente pro Instagram de quem comentou** (perfil, foto, destaques, lugar). Alvo: **50 a 100 contas tentadas**. Mínimo **50**. Se o teto morrer só em comentário, declara a lacuna e não fecha lead no escuro. Se o corpus não tiver 50 contas de alta sinal, amplia pra qualquer comentário com texto real (não emoji vazio) até 50. Não completa cota com "linda".

Docs de partida:

| Recurso | Doc |
|---|---|
| Perfil Instagram | https://docs.scrapecreators.com/v1/instagram/profile/ |
| Posts Instagram | https://docs.scrapecreators.com/v2/instagram/user/posts/ |
| Reels Instagram | https://docs.scrapecreators.com/v1/instagram/user/reels/ |
| Comentários Instagram | https://docs.scrapecreators.com/v2/instagram/post/comments/ |
| Destaques (highlights) | https://docs.scrapecreators.com/v1/instagram/user/highlights |
| Detalhe de um destaque | https://docs.scrapecreators.com/v1/instagram/user/highlight/detail |
| Busca YouTube | https://docs.scrapecreators.com/v1/youtube/search/ |
| Comentários YouTube | https://docs.scrapecreators.com/v1/youtube/video/comments/ |

Instagram e YouTube são o ponto de partida. Outra plataforma entra se ajudar a responder a pergunta. Não força plataforma só pra completar lista.

---

## 3. Montar um spy que ache mais que confirmação

Antes de gastar chamada: lê o briefing e o material que veio junto. Anota o que tá **definido**, o que é **hipótese**, o que é **desconhecido** e **qual decisão** a pesquisa vai apoiar.

### As quatro fontes

1. **Audiência própria**: relação com o expert e perguntas sobre a entrega dele.
2. **Concorrentes**: comunicação, convite, dúvida, experiência relatada, critério de comparação.
3. **Mercado amplo**: busca de solução, alternativa, linguagem, dificuldade, contraprova.
4. **Dados próprios**: quiz, atendimento, vendas. Registrar consentimento, período e de onde veio. **Não mandar esses dados pra API pública.**

### Famílias de busca

| Família | Molde (adapta ao assunto) |
|---|---|
| Problema e desejo | `[problema em linguagem de rua]` · `como [resultado desejado]` |
| Situação concreta | `[problema] + [rotina/contexto]` · `[solução] para iniciante` |
| Alternativa já tentada | `[alternativa] funciona` · `[alternativa] dificuldade` |
| Frustração e objeção | `[solução] não funcionou` · `[produto] dúvidas` · `[alternativa] vale a pena` |
| Consideração comercial | `[produto] preço` · `[programa] acompanhamento` · `[produto] acesso` |
| Mecanismo (se existir) | `[termo] como fazer` · `[termo] resultado` · `[termo] comparação` |

Molde orienta, não obriga rodar todos. A linguagem que aparece nos primeiros resultados refina os próximos. **Sempre** incluir pelo menos uma busca por dificuldade, discordância ou "tentei e não deu".

### Escolher conteúdo

Escolhe pelo que ajuda a entender a **pessoa**, não pelo que viralizou. Equilibra pergunta específica, relato de uso e convite comercial. Varia criador e situação. Não fica só no elogio nem só na treta.

Se o expert tem vídeo de **entrega** (treino, aula, demonstração), esse conteúdo entra. O convidado e os comments desse vídeo revelam a lead de oferta melhor que o vídeo de palco (celebridade, namoro, look).

Pra cada conteúdo, registra: **tema → promessa observada → convite/CTA → tipo de resposta → o que isso diz da lead.** Se só tem título ou legenda, não atribui ao vídeo roteiro, argumento ou CTA que ninguém viu.

---

## 4. Coletar e guardar a origem

Cada execução tem pasta própria. Não sobrescreve pesquisa anterior.

| Arquivo | O que tem |
|---|---|
| **Bruto** | Resposta da API como veio. Acesso restrito à pesquisa; log nunca captura credencial. |
| **Manifesto** | Data UTC, rota, parâmetros (sem segredo), cursor de entrada/saída, status, erro sanitizado, custo, arquivo e hash. |
| **Inventário** | Fonte, título/legenda, URL, em quais buscas e posições apareceu, métricas observadas, se coletou comentário. |
| **Corpus** | Plataforma, ID do comentário, ID/URL do conteúdo, texto original, autor pseudonimizado, flag de criador, data reportada, ponteiro pro bruto. |
| **Perfis** | `perfis-comentaristas.json`: handle, bio, followers, categoria, profissional, URL externa, endereço/cidade se a API der, privado/falha. |
| **Fotos** | `fotos-comentaristas/`: avatar baixado. URL do comment já serve; não gasta crédito só pra foto. |
| **Destaques** | Títulos (e capa) dos highlights das contas de alta sinal. Detalhe de um destaque só se o título for opaco e ainda couber no teto. |

Guarda também o resultado das buscas que **não** foram selecionadas. E o motivo de cada alvo escolhido.

Regras de registro:

- Data de observação separada da data de publicação. Data relativa ("há 2 semanas") é aproximada e fica marcada assim.
- Comentário completo fica no bruto. No relatório, o excerto é curto, contíguo e com contexto suficiente.
- Ordenação: anota a ordem pedida e a que deu pra verificar. Se data e sequência contradizem a recência pedida, marca "recência não confirmada". Não afirma que um parâmetro enviado reduziu viés.
- Parada: acabou o limite, acabaram as páginas relevantes, ou página nova parou de trazer situação nova. Explica a cobertura obtida. Repetição não prova saturação do mercado inteiro.

---

## 5. Auditar antes de descrever a pessoa

Antes de escrever uma linha sobre "quem é essa lead", passa a régua:

- **Deduplica** por plataforma + ID (ID com texto vazio também conta). Registro sem ID vai separado, com chave auxiliar documentada e sem alegar a mesma precisão.
- Em atualização, calcula recapturado, novo e união. Não soma página como se fosse gente nova.
- Conta comentário, conteúdo e conta **separadamente**. Não cruza identidade entre plataformas por nome parecido.
- Marca fala de criador e mostra como entrou (ou não) no denominador de audiência. Não deduz hierarquia de resposta que a API não dá.
- Separa: relato · pergunta · elogio · resposta de CTA · menção · interação sem texto · fora de escopo. Texto repetido sozinho não faz ninguém virar bot.
- Se for quantificar tema: publica regra, unidade e denominador. Regra de palavra-chave é sinal lexical, não leitura de necessidade.
- Olha **concentração**: um debate num post só, ou reclamação repetida de uma conta só, não vira prevalência.
- Comentário, view, like e longevidade **não** são venda, conversão nem escala. "Eu quero" puxado por CTA não prova compra. Like explosivo em post de identidade (celebridade, diploma, cidade) não prova lead de oferta.
- Conta pequena com pergunta de vaga, suporte ou uso **pesa mais** que conta grande só elogiando.
- **Não infere** idade, renda, religião, saúde ou diagnóstico por aparência, nome ou bio. Autodeclaração é relato, não censo. Foto e destaque descrevem o que **aparece** (academia, filho, logo de loja, cidade na bio). Isso é OBSERVED. Não vira "tem 28 anos, classe B".

---

## 6. Instagram de quem comentou (obrigatório)

**Não fecha persona só com o texto do comentário.** Depois do corpus, entra no Instagram das contas de alta sinal.

### Quem entra

Prioriza, nesta ordem:

1. Relato de uso, pergunta de oferta, suporte, preço, dificuldade, "tentei e não deu"
2. Fala específica de corpo, rotina, lugar, ofício
3. Repetiu em mais de um conteúdo

De fora da fila de perfil: emoji vazio, sticker sem texto, spam, conta do próprio criador. Elogio raso ("linda") só entra se ainda faltar gente pra chegar em 50.

Teto prático: **50 a 100 contas**. Menos que 50 é rodada incompleta, salvo se o corpus inteiro não tiver 50 handles únicos com texto. Não scrapa 200 elogios pra inflar número.

### O que puxar, nesta ordem de custo

1. **Foto de perfil** que já veio no comment. Baixa. **Olha.** Zero crédito.
2. **Perfil** (`/v1/instagram/profile`): bio, followers, following, posts, privado, professional/business, `category_name`, `external_url`, `business_address_json` se existir, `highlight_reel_count`.
3. **Destaques** (`/v1/instagram/user/highlights`): os **títulos** (Mãe, Treino, Trabalho, Antes/depois). Título já é sinal. Não gasta destaque nas 100 contas se o teto apertar: puxa em quem abriu e tem `highlight_reel_count` > 0, começando pelas de alta sinal, até caber. Detalhe (`/highlight/detail`) só em 3–8 contas em que o título não explica.
4. **Lugar:** bio, endereço de negócio, location nos posts. Uma página de posts (`/v2/instagram/user/posts`) nas **8 a 15** contas mais quentes, se ainda couber no teto.
5. Privado, apagado ou API vazia: conta a falha. Não preenche com chute.

### O que olhar na foto e nos destaques

OBSERVED, não diagnóstico:

- Como ela se põe: academia, espelho, biquíni, retrato formal, logo de ofício, criança, casa, carro
- Ofício visível: cabelo, cílios, loja, delivery, consultório, DJ
- Lugar visível: cidade na bio, encontro, "moro em X"
- Se a apresentação bate com a fala (crop de academia + "asfit ainda existe?" é ouro; logo de loja + pedido de vaga também)

Não inventa rotina a partir de um filtro. Selfie de academia não prova resultado.

### Lead ideal desta rodada

Com o cruzamento comentário + bio + foto + destaque + lugar, escreve **uma** composição pra briefing (não biografia, não fatia estatística):

- Situação (o que tenta resolver agora)
- Ofício e lugar que a evidência segura
- Como aparece na foto
- Fala literal (ID + URL)
- Objeção
- Qual peça conversa com ela
- Contraprova: quem interage por outro motivo (palco, look, treta)

A lead ideal é a conta que **demonstra interesse no problema/oferta** e cujo perfil abriu. Follower count baixo não desqualifica. Outlier de 50k não vira o avatar só por ser grande.

### Leads em uma linha (obrigatório)

Depois de olhar perfil, foto, destaques e lugar, cada conta tentada ganha **uma linha**. Sem parágrafo. Sem idade inventada. É o que o copy lê pra entender quem é cada uma.

Molde (nesta ordem, separado por ` · `):

`@handle · ofício e lugar que a bio/foto segura · o que a foto mostra · fala curta dela · sinal (vaga, uso, dor, look, palco)`

Quem não abriu: `@handle · perfil privado/apagado · fala: "…" · sinal`

O roster entra no relatório **logo após a lead ideal**, antes dos retratos situacionais. Contas de alta sinal primeiro. Elogio raso no fim, ou fora se só inflaria número.

---

## 7. Retratos situacionais da lead

Lê as falas **e** os perfis em contexto. Monta quantos recortes a evidência sustentar. Numa rodada exploratória, 2 a 4 retratos costumam organizar bem. Não preenche cota com variação artificial.

| Campo | Como preencher |
|---|---|
| **Nome do recorte** | Pela situação vivida. Sem personagem com idade e renda inventada. |
| **Contexto e tarefa** | O que tenta resolver e em que circunstância isso pesa. |
| **Dor concreta** | Episódio, ação, dificuldade observada. Rótulo tipo "baixa autoestima" não sobe sozinho. |
| **Desejo visível** | A mudança que ela declara querer e como reconheceria. |
| **Desejo profundo / tensão** | Interpretação apoiada em fala. Rotula como inferência. |
| **Tentativas e alternativas** | O que diz que fez, por que escolheu, o que aconteceu segundo ela. |
| **Barreiras e objeções** | O que dificulta começar, continuar, confiar ou contratar. |
| **Consciência** | Descreve o incômodo? Procura caminho? Compara solução? Avalia oferta? Sem presumir sequência universal. |
| **Gatilho de interesse** | Situação que faz ela prestar atenção. Marcar se foi relatada ou proposta. |
| **Linguagem real** | Excertos com ID de evidência e URL. Separados de paráfrase e de fala criada. |
| **Perfil observado** | Bio, foto, destaques, lugar. Handle. Followers. Privado/falha. |
| **Sinal comercial** | Interesse, uso relatado, pergunta sobre oferta, cadastro, compra. Explicitar o que tá confirmado. |
| **Contraprova e desconhecidos** | Exemplo que limita o retrato, encaixe incerto, pergunta em aberto. |

Retrato pode combinar situação de gente diferente e pode se sobrepor. É **composição pra briefing**, não biografia nem fatia estatística da base.

Prioriza por: pertinência à pergunta/produto · especificidade da fala · perfil aberto · sinal comercial observado. Explica o motivo da prioridade e a contraprova. Sem produto definido, prioriza clareza da necessidade.

Aponta também quem interage por outro motivo. "Interesse não confirmado" não é gente sem valor.

---

## 8. Pacote pra copy

Aqui vale a distinção: **lead-público** é o retrato da pessoa. **Lead de copy** é a abertura da peça. Esta skill entrega o primeiro. O segundo é trabalho da skill de redação.

Toda informação relevante recebe uma etiqueta:

- **OBSERVED**: fala, comportamento, foto, destaque ou conteúdo achado, com fonte. Acusação achada continua sendo acusação, não fato.
- **INFERRED**: interpretação apoiada em evidência, com o limite explicado.
- **GENERATED**: hipótese de ângulo, síntese criativa, cena composta. **Nunca** apresentada como voz literal de cliente.

O pacote em Markdown (JSON só se a integração pedir):

```
research_scope:     pergunta, fontes, período, limites e cobertura
fixed_context:      mecanismo, oferta, promessa e decisões que vieram prontas; desconhecidos em aberto
ideal_lead:         composição da lead desta rodada (comentário + perfil + foto)
leads_one_liners:   uma linha por conta (handle · ofício/lugar · foto · fala · sinal)
persona_slices:     retratos e evidências de cada um
voice_of_customer:  excerto literal + contexto + fonte + ID
objections:         dúvida/barreira + situação + evidências + contraprova
scenes:             momento / ação / consequência observados; composto marcado como GENERATED
angle_hypotheses:   recorte + tensão/desejo + entrada sugerida + evidências + limites
proofs_available:   o que existe, o que demonstra, de qual produto/fonte é
open_questions:     o que a pesquisa pública não resolveu
```

Pra cada hipótese de ângulo: com quem conversa, qual situação aborda, por que pode gerar interesse, qual evidência limita. Se sugere curiosidade, aponta a informação verdadeira que responde e onde a peça vai fechar isso. Se não existe, registra a lacuna.

Ângulo se relaciona com o mecanismo existente sem rebatizar, substituir ou inventar comprovação. Se ainda não tem mecanismo, entrega necessidade e ângulo de problema/desejo pra próxima etapa. **Spy não inventa mecanismo e chama de descoberta.**

---

## 9. Entrega e conferência

Relatório em Markdown, sem repetir conteúdo entre seções:

1. Lead ideal desta rodada (cruzamento comentário + perfil + foto), com limites claros.
2. **Leads em uma linha:** uma linha por conta tentada (50 a 100). Handle · ofício/lugar · foto · fala · sinal.
3. Spy de comunicação: conteúdo, convite, resposta, o que revela da pessoa.
4. Retratos situacionais: desejo, tentativa, objeção, perfil observado.
5. Banco de evidências + pacote pra copy.
6. Método: contagens, inventário, buscas exatas, fontes, perfis tentados vs abertos, lacunas.

PDF se pedir: briefing pra copy na frente (lead ideal, **roster em uma linha**, regras de voz, fotos com fala, recortes). Anexo com ID + URL. Link clicável. Conferir renderização e presença dos IDs. Foto da aluna entra no briefing, não só no anexo.

Antes de fechar, confere: amostra de excerto contra o bruto · aritmética da deduplicação · vínculo conclusão → ID → fonte · cada retrato aponta pelo menos um perfil olhado ou declara que o perfil não abriu. Atenção dobrada em recorte que muda sentido, tradução, resultado atribuído a várias intervenções e exemplo contrário à hipótese preferida.

---

## Regras inegociáveis

1. **JAMAIS inventar** comentário, frase, número, persona ou demografia. Sem evidência, é hipótese marcada como hipótese.
2. Toda fala do público carrega **ID + URL**. Sem isso não sobe pro relatório.
3. Comentário de concorrente é do concorrente. **Não vira prova do nosso produto.**
4. Comentário público informa a pesquisa. **Não vira depoimento autorizado pra anúncio.**
5. Chave de API fica fora de tudo: skill, briefing, relatório, log, print.
6. **Não fecha lead só com texto de comentário.** Sempre tenta o Instagram de **50 a 100 contas** (bio, foto, destaques, lugar) antes de descrever a pessoa. Menos que 50 tentadas, sem o corpus ter acabado, é rodada incompleta.
