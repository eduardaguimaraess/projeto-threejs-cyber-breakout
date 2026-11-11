# Cyber Breakout — Labirinto Sci-Fi Top-Down

Experiência interativa universitária feita com Three.js. Na tela inicial, clique em **Jogar** para começar. Atravesse os três setores, colete três chaves em cada um, evite quatro sentinelas em patrulha e entre no buraco negro brilhante no final para voltar à tela inicial. O disco hover luminoso acelera com Shift. A névoa escura limita a visão e a câmera acompanha a personagem.

> **Integrante:** Eduarda Guimarães Monteiro. O enunciado especifica grupos de 5 a 7 integrantes; confirmar com a instituição como proceder com grupo individual.

## Revisão dos requisitos do enunciado

| Requisito | Situação nesta cópia |
|---|---|
| Três setores temáticos identificáveis | Atendido: perímetro, núcleo e singularidade. |
| Pelo menos 20 elementos e 8 tipos | Atendido pelo cenário procedural; luminárias, consoles, telas, balizadores, avatar, sentinelas, chaves, portas e singularidade. O código registra a contagem no console. |
| Câmera, iluminação, piso e navegação OrbitControls | Implementados. OrbitControls permite órbita horizontal e zoom. |
| Chaves e progressão por setor | Implementadas: há três chaves em cada setor e os portais de avanço ficam bloqueados até a coleta completa. |
| Tela inicial com botão Jogar | Implementada; a simulação fica pausada até iniciar. |
| Três texturas visíveis | Implementadas como três mapas `CanvasTexture` distintos para piso, painéis e consoles/caixas. Não há imagens de textura externas incluídas. |
| Três modelos externos GLB/GLTF funcionando | Atendido: três robôs GLB licenciados como CC0 são carregados e distribuídos entre quatro sentinelas. O portal e avatar são procedurais. |
| Três capturas de evidência | Atendido nesta pasta: `setor-01.jpeg`, `setor-02.jpeg` e `setor-03.jpeg` mostram os três setores; há também `inicio.jpeg`. |
| README com integrantes e créditos reais | Nome da integrante e fontes/licenças dos modelos listados abaixo. A composição individual do grupo diverge da faixa de 5 a 7 indicada no enunciado. |

Assim, os modelos externos, créditos e capturas dos três setores estão presentes nesta pasta. Antes do envio, ainda é preciso confirmar com a instituição como proceder com grupo individual, preparar o ZIP e validar uma cópia extraída.

## Controles

- **W:** frente (topo da tela); **A:** esquerda; **S:** para trás; **D:** direita. As setas também movem. **Shift:** acelera o disco hover.
- **Chaves:** colete as três no setor para liberar a passagem ao próximo. A singularidade final também exige as três chaves do hangar.
- **Sentinelas:** colisões retornam ao início do setor atual; as chaves coletadas permanecem com a personagem.
- **Mouse arrastado:** orbitar a câmera em volta do avatar.
- **R:** reiniciar a posição no começo.
- **Roda do mouse:** zoom.

## Setores

1. **Entrada / Perímetro de Segurança (ciano):** primeiro trecho de um labirinto denso e ortogonal, com paredes blindadas e lanternas ciano montadas junto às paredes. Colete as três chaves para abrir a passagem leste.
2. **Núcleo de Servidores e Processamento (magenta/violeta):** corredores compactos com consoles biométricos, lanternas magenta e sentinelas em patrulha. Colete as três chaves para avançar.
3. **Setor da Singularidade (âmbar):** labirinto final; depois de coletar suas três chaves, entre no buraco negro para retornar à tela inicial.

Os três ambientes são contínuos em uma única planta. Cada setor tem uma malha própria de corredores gerada por busca aleatória e três chaves distribuídas pelos centros das células. Os dois portais de avanço verificam se as três chaves do setor anterior foram coletadas. Quatro sentinelas fazem patrulhas; ao encostar numa, a personagem retorna ao começo do setor atual e mantém as chaves. O portal final é uma singularidade luminosa: ao entrar nela com as três chaves do último setor, a página recarrega e retorna à tela inicial. A câmera é uma PerspectiveCamera quase vertical; fog escuro e luminárias coloridas montadas junto às paredes mantêm a visibilidade concentrada. Ciano, magenta e âmbar distinguem os setores.

## Elementos 3D catalogados

Cada instância independente é contabilizada como um elemento. Chão principal, paredes estruturais, luzes, câmera e HUD não são contados. O código contém mais de 20 instâncias e pelo menos 8 tipos.

| # | Tipo | Quantidade aproximada | Setor(es) |
|---:|---|---:|---|
| 1 | Luminária de parede | 6 | Todos |
| 2 | Console biométrico | 6 | Todos |
| 3 | Tela holográfica de acesso | 6 | Todos |
| 4 | Balizador luminoso dos portais | 12 | Transições |
| 5 | Personagem jogável (disco hover ciano e magenta) | 1 | Todos |
| 6 | Sentinela robótica importada (três modelos GLB, quatro instâncias) | 4 | Todos |
| 7 | Chave coletável | 9 | 3 por setor |
| 8 | Porta energética de progressão | 2 | Entre setores |
| 9 | Singularidade / buraco negro | 1 | Setor 03 |

As paredes estruturais não entram na contagem do enunciado. Os consoles, telas, luminárias, balizadores, personagem, sentinelas, chaves e singularidade fornecem pelo menos oito tipos de elementos independentes. O console do navegador informa o total contabilizado.

## Modelos externos GLB

Os três modelos são carregados com `GLTFLoader`, ajustados automaticamente à altura dos corredores e reutilizados entre as quatro patrulhas. As fontes publicam os modelos sob CC0 (domínio público); os créditos estão registrados aqui mesmo sem obrigação legal de atribuição.

| Arquivo | Modelo / fonte | Licença |
|---|---|---|
| `models/sentinela.glb` | [Humanoid robot standing — Innerscene](https://www.innerscene.com/tools/library/3d-parts/humanoid-robot-standing-f4186ca5) | CC0 |
| `models/sentinela-bronze.glb` | [Toy robot — Innerscene](https://www.innerscene.com/tools/library/3d-parts/toy-robot-22ca7494) | CC0 |
| `models/sentinela-companion.glb` | [Desk companion robot — Innerscene](https://www.innerscene.com/tools/library/3d-parts/desk-companion-robot-f2d0b656) | CC0 |

## Texturas

O jogo gera três mapas `CanvasTexture` independentes durante a inicialização: grade metálica para o piso, painéis segmentados para as paredes e padrão diagonal para consoles/caixas. Eles são criados localmente pelo código e não dependem de arquivos de imagem ou de fontes externas. A pasta `textures/` está vazia nesta versão.

## Executar no VS Code

1. As três texturas são geradas por Canvas; os três modelos GLB estão incluídos em `models/` e são carregados pelo jogo.
2. Abra esta pasta no Visual Studio Code.
3. Instale a extensão **Live Server**, clique com o botão direito em `index.html` e escolha **Open with Live Server**.
4. Abra o endereço local no navegador. Evite abrir o HTML com `file://`, pois ES Modules e recursos relativos precisam de servidor local.
5. Verifique no console do navegador a contagem de elementos; as três texturas Canvas são geradas durante a inicialização.

Three.js e OrbitControls são carregados via ES Modules do jsDelivr; é necessária conexão à internet para iniciar. Nenhum pacote npm ou `node_modules` é necessário.

## Evidências e entrega

As capturas dos três setores já estão em `evidencias/` como `setor-01.jpeg`, `setor-02.jpeg` e `setor-03.jpeg`; `inicio.jpeg` registra a tela inicial. Inclua no ZIP `index.html`, `README.md`, `models/`, `textures/` e `evidencias/`. Teste a cópia extraída em outra pasta antes de enviar pelo AVA.

## Créditos dos ativos

Os três modelos robóticos estão listados acima com suas fontes e licenças CC0. O projeto não inclui modelos de licença CC BY.
