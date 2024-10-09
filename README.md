Stage Manager (Stage)
   ├── Layer Manager (Layer)
   │   └── Agregador (Aggregator)
   │       ├── Reta (Line)
   │       ├── Ponto (Point)
   │       ├── Segmento de Reta (Line Segment)
   │       ├── Ponto Médio (Middle Point)
   │       ├── Circunferência (Circumference)
   │       │   └── CircumferenceComponent (herda de Component)
   │       └── Ponto de Interseção (Intersection Point)
   └── Parser Orchestrator
           ├── Coordena o parsing e criação de objetos
             O parsing no contexto do arquivo `parser-orchestrator.js` acontece principalmente na função `orchestrate()`, que é responsável por processar as linhas de dados de arquivos GEO e construir os objetos geométricos correspondentes no sistema.

Como o parsing ocorre:

1. Entrada de Dados:
   - A função `orchestrate()` recebe um array `vec_dynamic_obj` que contém objetos dinâmicos com identificadores e informações parseadas. Além disso, utiliza `this.mapArr`, que armazena os dados a serem processados, contendo as propriedades de cada elemento geométrico.

2. Processamento das Linhas:
   - Para cada item em `this.mapArr`, a função verifica se há dados válidos e, em seguida, chama o método `do()` para processar e criar os objetos geométricos apropriados com base no tipo de elemento (circunferência, ponto, etc.).

3. Criação de Objetos Geométricos:
   - O método `do()` é responsável por analisar cada entrada, identificando o tipo de objeto (usando `ELEMENTS_CLASS`) e chamando o modelo correspondente (por exemplo, `CircumferenceModel`, `PointModel`, etc.) para instanciar o objeto.
   - O parsing individual de cada linha é realizado através das informações armazenadas no `map`, que representa as propriedades do objeto a ser criado.

4. Desenho e Configuração:
   - Após a criação dos objetos, o método `draw()` é chamado para desenhar os elementos geométricos no sistema. 

Portanto, o parsing está integrado ao fluxo de `orchestrate()`, onde os dados são analisados, interpretados e transformados em objetos geométricos prontos para uso.
           ├── Utiliza modelos como:
           │   ├── PointModel
           │   ├── MiddlePointModel
           │   ├── CircumferenceModel
           │   ├── LineSegmentModel
           │   ├── LineModel
           │   └── IntersectionModel
           ├── Interage com elementos via menu.tools
           └── Chama métodos `do()` e `draw()` para manipulação dos objetos
