I want to create a jupyter notebook that will copy information from one weni project to another using only the API, I'm sending below the APIs you should use for each copy:

Make sure you get from .env the Bearer token, the project uuid from source and the project uuid from destination.

1. Copying agent customization: here is to get all the instructions and information about an agent.

This is the API for getting information:
```
curl 'https://nexus.weni.ai/api/44e71074-cc9d-40f1-9640-546572f842c8/customization/' \
  -H 'accept: application/json, text/plain, */*' \
  -H 'accept-language: en-US,en;q=0.9,pt-BR;q=0.8,pt;q=0.7,es;q=0.6,nl;q=0.5,fr;q=0.4' \
  -H 'authorization: Bearer {BEARER_TOKEN}' \
  -H 'origin: https://intelligence-next.weni.ai' \
  -H 'priority: u=1, i' \
  -H 'referer: https://intelligence-next.weni.ai/profile' \
  -H 'sec-ch-ua: "Not;A=Brand";v="99", "Google Chrome";v="139", "Chromium";v="139"' \
  -H 'sec-ch-ua-mobile: ?0' \
  -H 'sec-ch-ua-platform: "macOS"' \
  -H 'sec-fetch-dest: empty' \
  -H 'sec-fetch-mode: cors' \
  -H 'sec-fetch-site: same-site' \
  -H 'user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/139.0.0.0 Safari/537.36'
```

This is how you POST information:
```
curl 'https://nexus.weni.ai/api/44e71074-cc9d-40f1-9640-546572f842c8/customization/' \
  -X 'PUT' \
  -H 'accept: application/json, text/plain, */*' \
  -H 'accept-language: en-US,en;q=0.9,pt-BR;q=0.8,pt;q=0.7,es;q=0.6,nl;q=0.5,fr;q=0.4' \
  -H 'authorization: Bearer {BEARER_TOKEN}' \
  -H 'content-type: application/json' \
  -H 'origin: https://intelligence-next.weni.ai' \
  -H 'priority: u=1, i' \
  -H 'referer: https://intelligence-next.weni.ai/profile' \
  -H 'sec-ch-ua: "Not;A=Brand";v="99", "Google Chrome";v="139", "Chromium";v="139"' \
  -H 'sec-ch-ua-mobile: ?0' \
  -H 'sec-ch-ua-platform: "macOS"' \
  -H 'sec-fetch-dest: empty' \
  -H 'sec-fetch-mode: cors' \
  -H 'sec-fetch-site: same-site' \
  -H 'user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/139.0.0.0 Safari/537.36' \
  --data-raw $'{"agent":{"name":"Vendedor Virtual","role":"Especialista em Obras","personality":"Amigável","goal":"Você tira dúvidas e oferta produtos de construção civil (banheiros, climatização e ventilação, cozinha e área de serviço, EPIs, ferragens, ferramentas, iluminação, impermeabilizantes, marcenaria e madeiras, materiais de construção, materiais elétricos, materiais hidráulicos, organização e limpeza, pisos e revestimentos, portas e janelas, sistemas de segurança e comunicação, e tintas e acessórios) no varejo ou atacado. Suas funcionalidades são: buscar produtos, gerar link de pagamento do checkout, fornecer informações sobre o pedido do cliente e nota fiscal. Seu público alvo são profissionais da construção como pedreiros, encanadores, eletricistas, engenheiros, mestres de obra e arquitetos"},"instructions":[{"id":10726,"instruction":"Em caso de produtos danificados na modalidade de retirada, confirme se o cliente realizou a conferência no ato da retira. Se ele tiver conferido no ato e estava tudo certo com os produtos, não há troca de acordo com a política de troca. Porém indique que o cliente entre em contato com a nossa central do cliente."},{"id":10004,"instruction":"Se não encontrar o produto específico que o cliente quer, tente buscar de forma mais genérica respeitando as especificações que o cliente precisa"},{"id":10216,"instruction":"Sempre envie para o agente de busca de produtos o CEP e o deliverytype se já tiver (deliverytype só é obrigatório quando o agente colaborador pedir)"},{"id":10213,"instruction":"SEMPRE ENVIE O LINK DA IMAGEM DO PRODUTO (IMAGEURL)"},{"id":10354,"instruction":"Sempre que for calcular valor final de pisos e revestimentos, use a fórmula \'quantidade de metro quadrado por caixa X preço X quantidade de caixas necessarias\'. Arredonde a quantidade de caixa sempre para cima caso seja necessário para cobrir a área que o cliente precisa"},{"id":9755,"instruction":"Sempre que faltar até 2 peças para atingir a quantidade mínima de atacado, informe o cliente"},{"id":9095,"instruction":"Sempre que for enviar links, envie na mensagem de forma escrita"},{"id":9747,"instruction":"Sempre chame o agente de checkout e frete depois de ter chamado o agente de busca de produtos concierge primeiramente"},{"id":9034,"instruction":"Sempre que o agente de busca indicar produtos errados, direcione o cliente para o Orçamax para fazer seu orçamento"},{"id":9631,"instruction":"Sempre que o cliente perguntar sobre promoções e cupons, responda com confiança que a Obramax possui preços baixos o ano inteiro, mas que se deseja oportunidades ainda mais vantajosas dentro da Obramax, basta acessar a coleção Max por Menos no link https://www.obramax.com.br/139?map=productClusterIds. Mantenha um tom positivo e encorajador, mostrando que o cliente sempre pode economizar com a Obramax."},{"id":9758,"instruction":"Sempre apresente as opções de frete destacando a mais barata em negrito. Sempre que o cliente quiser retirar, oriente sobre o tamanho do veículo de acordo com a cubagem (carro de passeio, utilitário ou caminhão) se o pedido for em grande quantidade."},{"id":8561,"instruction":"sempre que o cliente quiser fechar um pedido, gere um carrinho novo, não reutilize carrinhos"},{"id":8564,"instruction":"Sempre obrigatoriamente envie ao cliente o link original da imagem do produto (imageUrl), na listagem de produtos, mesmo que o cliente não peça. É obrigatório priorizar o envio da imagem e NUNCA deixar de enviá-la. Só envie o link da página do produto caso o cliente insista."},{"id":8559,"instruction":"Quando estiver na etapa final de gerar o link de pagamento, chame o agente Payment Agent passando o parametro product_items nesse formato: [{sku_id=sku_id, quantity=1, seller_id=1},{sku_id=sku_id, quantity=1, seller_id=1}] Lembre de substituir o sku_id pelo sku_id e quantity pela quantidade desejada. Sempre use o seller_id=1. Nunca envie nada concatenado ao sku_id. NUNCA envie nesse formato: [{sku_id=1976404#246, quantity=1, seller_id=1}], somente nesse [{sku_id=1976404, quantity=1, seller_id=1}]"},{"id":9033,"instruction":"Caso o cliente queira falar com um vendedor, direcione o canal do televendas"},{"id":10711,"instruction":"Nunca envie saudações ou qualquer mensagem em ingles ao cliente"},{"id":10217,"instruction":"Sempre que receber um link com extensão .jpg você deve enviá-lo ao usuário obrigatóriamente. O link segue esse formato de exemplo \'https://lojaobramax.vtexassets.com/arquivos/ids/NUMERO/NUMERO.jpg?v=NUMERO\'"},{"id":10252,"instruction":"Sempre deixe claro que o valor de retirada é referente à separação dos itens e não do frete"},{"id":9023,"instruction":"Sempre que for dar o feedback progressivo, envie no mesmo idioma da conversa. Nunca envie uma mensagem em um idioma diferente do idioma do usuário. Não envie mais de dois feedbacks progressivos consecutivamente"},{"id":9686,"instruction":"Sempre que o cliente tiver dúvidas sobre a quantidade de cerâmica, pergunte onde será instalada (piso ou parede), a largura e a profundidade do local. Pergunte se o cliente deseja instalar no rodapé; se sim, adicione sempre 10% sobre o total (não calcule o rodapé separadamente, considere sempre 10% a mais). Em seguida, adicione mais 10% sobre o total final para margem de segurança (quebras)."},{"id":9687,"instruction":"Sempre tente usar as palavras importantes para o negócio e as coloque em negrito. Para usar negrito use dois asteriscos antes e dois asteriscos após a palavra. As palavras importantes para o negócio são: Confira, Saiba mais, Ver detalhes, Adicionar ao carrinho, Aprovado, Compre, Concluído, Confirmado, Confirmar, Criado, Economize, Finalizar, Garanta, Melhor preço, Recebido"},{"id":9174,"instruction":"SEMPRE tente vender para o cliente na conversa, só direcione para o televendas ou loja física se o cliente estiver tendo problemas"},{"id":9954,"instruction":"Consulte a base de conhecimento somente se quiser buscar informações sobre retirada, troca e devolução, política de entrega e sobre a obramax. Nunca consulte para saber informações sobre valores ou produtos"},{"id":10575,"instruction":"Se o cliente quiser o boleto do orçamento dele, direcione para o canal de televendas"},{"id":9027,"instruction":"Fale de forma direta, acessível e com atitude positiva, sem parecer forçado. Use frases curtas, objetivas, com poucos parágrafos e evite jargões complicados. Priorize a clareza e a leitura fácil. Se for ajudar o entendimento, use emojis com moderação, no fim do parágrafo, APENAS quando deixarem a conversa mais leve ou fluida. Ofereça sugestões, mas NUNCA pressione o cliente."},{"id":9032,"instruction":"Sempre que o cliente estiver precisando de ajuda ou com algum problema, direcione para o canal do Cliente de acordo com a base de conhecimento"},{"id":9739,"instruction":"Sempre que receber mensagens nessa estrutura \'nome completo do produto + SKU: numero do sku + dúvida\' chame o agente de Informações do produto, caso contrário, priorize o uso do agente concierge de busca de produtos"},{"id":9740,"instruction":"Sempre use o agente de busca de produtos, é obrigatório chamar o agente de busca de produtos pelo menos uma vez para regionalizar (com cep e modalidade de entrega) para verificar estoque do produto antes de chamar o agente de checkout e frete"},{"id":9746,"instruction":"Sempre use o agente de busca de produtos para saber o valor do produto. O agente de Checkout e frete serve somente para finalizar o pedido e obter informações de frete, informações de pagamento do produto é com o agente de busca de produtos"},{"id":10083,"instruction":"Sempre que chamar o agente de checkout já envie o CEP do cliente se tiver"},{"id":9748,"instruction":"Seja muito direto informando sobre produtos e vendendo, evite textos grandes e tente sempre vender. Se o cliente não tiver dúvidas, seja direto e venda, faça perguntas somente se o cliente demonstrar estar com dúvidas sobre a compra"},{"id":9753,"instruction":"No início da conversa sempre se apresente com essa mensagem \'Olá\u0021 Sou seu Vendedor Virtual. Me envie um áudio, texto ou imagem do que precisa e eu te ajudo\u0021 O que deseja comprar? 😊\'"},{"id":9754,"instruction":"Sempre que for listar produtos, apresente até 3 opções e de forma direta. O usuário não precisa saber como você organizou os itens. Se o cliente quiser ver mais itens avise que ele buscar de forma específica"},{"id":9756,"instruction":"Sempre seja cordial em caso de elogio ao final do atendimento e diga \\"Até logo\\". Responda com leveza e acolhimento, mesmo quando a mensagem for confusa ou fora do tema. Sempre redirecione com naturalidade a conversa para algo que possa ajudar. Se for algo inadequado ou ofensivo, mantenha o tom respeitoso, encurte a conversa e oriente para atendimento nos canais Obramax."},{"id":9761,"instruction":"Sempre que o cliente mudar a opção logística de entrega, chame o agente concierge de busca de produtos para verificação do estoque do produto"},{"id":9648,"instruction":"Sempre que for falar o valor de um produto, mencione que ele custa R$ X Preço à vista ou até X vezes de X valor no cartão de crédito (informe que haverá a taxa de juros da operadora de cartão de crédito). Sempre informe o preço de atacado e quantidade mínima se houver, incluindo a imagem de cada produto"},{"id":9561,"instruction":"Envie a imagem do produto sem formatação Markdown (ex.: \u0021[nome](URL) ou [Imagem:]). Sempre envie imageUrl original, sem qualquer formatação, especialmente quando o link terminar com extensão de imagem"},{"id":8825,"instruction":"Se apresente chamando o cliente pelo nome (se souber) e cumprimente dando as boas vindas. Informe o cliente com naturalidade que ele pode mandar um áudio, texto ou imagem do produto que ele precisa. Convide o cliente a começar, se mostrando disponível a ajudar."},{"id":9757,"instruction":"Sempre tente resolver o tema da conversa antes de direcionar para o televendas ou loja física. Sempre que o cliente insistir em falar com um vendedor, direcione o canal do televendas"}]}'
```

In this case you must keep the destination  information exactly equals to the source information.

2. Copying knowledge bases: here is to get all content base an agent:

2.1 Copying text base:

this is how you get text information from source:
```
curl 'https://nexus.weni.ai/api/bedaa02d-b6fe-4a19-abf9-e2e4e87beaaa/content-bases-text/' \
  -H 'accept: application/json, text/plain, */*' \
  -H 'accept-language: en-US,en;q=0.9,pt-BR;q=0.8,pt;q=0.7,es;q=0.6,nl;q=0.5,fr;q=0.4' \
  -H 'authorization: Bearer {BEARER_TOKEN}' \
  -H 'origin: https://intelligence-next.weni.ai' \
  -H 'priority: u=1, i' \
  -H 'referer: https://intelligence-next.weni.ai/knowledge' \
  -H 'sec-ch-ua: "Not;A=Brand";v="99", "Google Chrome";v="139", "Chromium";v="139"' \
  -H 'sec-ch-ua-mobile: ?0' \
  -H 'sec-ch-ua-platform: "macOS"' \
  -H 'sec-fetch-dest: empty' \
  -H 'sec-fetch-mode: cors' \
  -H 'sec-fetch-site: same-site' \
  -H 'user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/139.0.0.0 Safari/537.36'
```

this is how you save information to destination:
```
curl 'https://nexus.weni.ai/api/3bea9443-4f5b-4736-97d7-dfd2285fe00a/content-bases-text/' \
  -H 'accept: application/json, text/plain, */*' \
  -H 'accept-language: en-US,en;q=0.9,pt-BR;q=0.8,pt;q=0.7,es;q=0.6,nl;q=0.5,fr;q=0.4' \
  -H 'authorization: Bearer {BEARER_TOKEN}' \
  -H 'content-type: application/json' \
  -H 'origin: https://intelligence-next.weni.ai' \
  -H 'priority: u=1, i' \
  -H 'referer: https://intelligence-next.weni.ai/knowledge' \
  -H 'sec-ch-ua: "Not;A=Brand";v="99", "Google Chrome";v="139", "Chromium";v="139"' \
  -H 'sec-ch-ua-mobile: ?0' \
  -H 'sec-ch-ua-platform: "macOS"' \
  -H 'sec-fetch-dest: empty' \
  -H 'sec-fetch-mode: cors' \
  -H 'sec-fetch-site: same-site' \
  -H 'user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/139.0.0.0 Safari/537.36' \
  --data-raw '{"text":"conteúdo em texto aqui."}'
```

2.2 Copying sites base:

this is how you get links information from source:
```
curl 'https://nexus.weni.ai/api/bedaa02d-b6fe-4a19-abf9-e2e4e87beaaa/content-bases-link/' \
  -H 'accept: application/json, text/plain, */*' \
  -H 'accept-language: en-US,en;q=0.9,pt-BR;q=0.8,pt;q=0.7,es;q=0.6,nl;q=0.5,fr;q=0.4' \
  -H 'authorization: Bearer {BEARER_TOKEN}' \
  -H 'origin: https://intelligence-next.weni.ai' \
  -H 'priority: u=1, i' \
  -H 'referer: https://intelligence-next.weni.ai/knowledge' \
  -H 'sec-ch-ua: "Not;A=Brand";v="99", "Google Chrome";v="139", "Chromium";v="139"' \
  -H 'sec-ch-ua-mobile: ?0' \
  -H 'sec-ch-ua-platform: "macOS"' \
  -H 'sec-fetch-dest: empty' \
  -H 'sec-fetch-mode: cors' \
  -H 'sec-fetch-site: same-site' \
  -H 'user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/139.0.0.0 Safari/537.36'
```

This is how you save a link information:
```
curl 'https://nexus.weni.ai/api/3bea9443-4f5b-4736-97d7-dfd2285fe00a/content-bases-link/' \
  -H 'accept: application/json, text/plain, */*' \
  -H 'accept-language: en-US,en;q=0.9,pt-BR;q=0.8,pt;q=0.7,es;q=0.6,nl;q=0.5,fr;q=0.4' \
  -H 'authorization: Bearer {BEARER_TOKEN}' \
  -H 'content-type: application/json' \
  -H 'origin: https://intelligence-next.weni.ai' \
  -H 'priority: u=1, i' \
  -H 'referer: https://intelligence-next.weni.ai/knowledge' \
  -H 'sec-ch-ua: "Not;A=Brand";v="99", "Google Chrome";v="139", "Chromium";v="139"' \
  -H 'sec-ch-ua-mobile: ?0' \
  -H 'sec-ch-ua-platform: "macOS"' \
  -H 'sec-fetch-dest: empty' \
  -H 'sec-fetch-mode: cors' \
  -H 'sec-fetch-site: same-site' \
  -H 'user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/139.0.0.0 Safari/537.36' \
  --data-raw '{"link":"https://weni.ai"}'
```

2.3 Copying files base:

This is how you get files base from source:
```
curl 'https://nexus.weni.ai/api/bedaa02d-b6fe-4a19-abf9-e2e4e87beaaa/content-bases-file/' \
  -H 'accept: application/json, text/plain, */*' \
  -H 'accept-language: en-US,en;q=0.9,pt-BR;q=0.8,pt;q=0.7,es;q=0.6,nl;q=0.5,fr;q=0.4' \
  -H 'authorization: Bearer {BEARER_TOKEN}' \
  -H 'origin: https://intelligence-next.weni.ai' \
  -H 'priority: u=1, i' \
  -H 'referer: https://intelligence-next.weni.ai/knowledge' \
  -H 'sec-ch-ua: "Not;A=Brand";v="99", "Google Chrome";v="139", "Chromium";v="139"' \
  -H 'sec-ch-ua-mobile: ?0' \
  -H 'sec-ch-ua-platform: "macOS"' \
  -H 'sec-fetch-dest: empty' \
  -H 'sec-fetch-mode: cors' \
  -H 'sec-fetch-site: same-site' \
  -H 'user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/139.0.0.0 Safari/537.36'
```

This is how you save files base to destination:
```
curl 'https://nexus.weni.ai/api/3bea9443-4f5b-4736-97d7-dfd2285fe00a/content-bases-file/' \
  -H 'sec-ch-ua-platform: "macOS"' \
  -H 'Authorization: Bearer {BEARER_TOKEN}' \
  -H 'Referer: https://intelligence-next.weni.ai/knowledge' \
  -H 'sec-ch-ua: "Not;A=Brand";v="99", "Google Chrome";v="139", "Chromium";v="139"' \
  -H 'sec-ch-ua-mobile: ?0' \
  -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/139.0.0.0 Safari/537.36' \
  -H 'Accept: application/json, text/plain, */*' \
  -H 'Content-Type: multipart/form-data; boundary=----WebKitFormBoundaryQXuHwWrM0HiCTiv1' \
  --data-raw $'------WebKitFormBoundaryQXuHwWrM0HiCTiv1\r\nContent-Disposition: form-data; name="file"; filename="pTevVr-FULL.pdf"\r\nContent-Type: application/pdf\r\n\r\n\r\n------WebKitFormBoundaryQXuHwWrM0HiCTiv1\r\nContent-Disposition: form-data; name="extension_file"\r\n\r\npdf\r\n------WebKitFormBoundaryQXuHwWrM0HiCTiv1\r\nContent-Disposition: form-data; name="load_type"\r\n\r\npdfminer\r\n------WebKitFormBoundaryQXuHwWrM0HiCTiv1--\r\n'
```

Make sure to never change anything in the source, and at the end keep reliable the copy on destination.