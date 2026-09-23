[[EXEMPLOS-PRÁTICOS DE FRAMEWORKS PARA DESENVOLVIMENTO DE SOFTWARE]]
#ASSUNTO 
## Visão geral

O estudo de desenvolvimento de software moderno exige a compreensão de **frameworks**, que atuam como estruturas padronizadas para acelerar a criação, manutenção e escalabilidade de aplicações. Esta nota aborda desde os conceitos elementares de arquitetura de software (reuso, inversão de controle e injeção de dependências) até a persistência de dados utilizando mapeamento objeto-relacional (ORM), passando pelo ecossistema de frameworks corporativos (Spring e Java EE), desenvolvimento mobile (Android Studio, Kotlin e ciclo de vida de Activities) e os principais frameworks para web do mercado nas linguagens JavaScript, PHP e Python.

---

## Conceitos principais

Para dominar a matéria, você precisa compreender claramente estes conceitos fundamentais:

- **Framework (Arcabouço):** Um esqueleto ou conjunto de classes que constitui um projeto abstrato. Fornece uma estrutura rígida, regras padronizadas e componentes reutilizáveis para solucionar problemas de um domínio específico, invertendo o controle da aplicação.
- **API (Interface de Programação de Aplicativos):** Conjunto de regras e protocolos que permite a troca de dados e a comunicação direta entre sistemas distintos, operando em uma lógica de pergunta-resposta (cliente-servidor).
- **Inversão de Controle (IoC):** Princípio de design de software em que a responsabilidade de controlar o fluxo de execução e verificar os eventos do sistema é transferida do próprio componente de código para uma estrutura externa maior (o framework ou container).
- **Injeção de Dependências (DI):** Padrão de desenvolvimento no qual os componentes de um sistema não instanciam manualmente suas dependências; em vez disso, eles recebem essas dependências automaticamente de uma entidade externa (como o container do framework).
- **Beans:** Instâncias de classes Java que são criadas, gerenciadas, conectadas e destruídas pelo container do framework (como o Spring), promovendo o acoplamento fraco.
- **ORM (Mapeamento Objeto-Relacional):** Técnica e ferramenta que atua como tradutora entre o paradigma orientado a objetos (do código) e o modelo relacional (do banco de dados), associando classes a tabelas e atributos a colunas de forma declarativa.
- **AOP (Programação Orientada a Aspectos):** Paradigma que complementa a Orientação a Objetos, focado em modularizar **preocupações transversais** (funcionalidades que atravessam várias partes do sistema, como registros de logs, controle de transações, segurança e auditoria) para evitar a repetição de código.
- **Componente:** Uma parte substituível, executável e independente de um sistema que oculta seus detalhes de implementação e expõe interfaces para realizar funções.
- **Plataforma:** Ambiente integrado que distribui padrões de software e serve como base física ou digital para programar em uma linguagem utilizando frameworks e APIs.

---

## Conteúdo explicado

### 1. Fundamentos de Engenharia de Software Aplicados a Frameworks

Os frameworks são construídos sobre os pilares da **Programação Orientada a Objetos (POO)**:

1. **Abstração de Dados:** Permite interagir com as informações sem precisar conhecer os detalhes físicos de onde e como elas estão armazenadas. _Exemplo:_ Utilizar comandos SQL para buscar dados sem saber em que parte do disco eles residem.
2. **Polimorfismo:** Capacidade de diferentes objetos responderem a uma mesma mensagem de maneiras distintas. Manifesta-se frequentemente através da **sobrecarga de métodos (Overload)**, na qual um método é definido várias vezes com conjuntos de parâmetros diferentes.
3. **Herança:** Promove o reuso de código ao permitir que classes derivadas (subclasses) herdem métodos e atributos de uma classe base (superclasse), podendo estendê-los.

A utilização dessas ferramentas equilibra uma balança de custo-benefício:

- **Vantagens:** Economia de tempo a longo prazo, maior consistência, redução de linhas de código repetitivas (princípio **DRY - Don't Repeat Yourself**), facilidade nos testes e foco exclusivo na lógica de negócio.
- **Custos/Desafios:** Curva de aprendizado acentuada, código mais difícil de depurar devido à complexidade interna do framework e necessidade de mão de obra especializada.

---

### 2. O Ecossistema Spring Framework

O Spring é um framework open-source altamente modular, essencial para o desenvolvimento de aplicações Java corporativas. Ele é estruturado em torno do seu **Container**, que gerencia o ciclo de vida dos **beans**.

#### Componentes Fundamentais do Container Spring:

- **Core:** Fornece a base do framework e implementa o controle dos _classloaders_ (que transformam arquivos compilados para que a JVM os compreenda).
- **Beans:** Contém a especificação `BeanFactory`, responsável pelo controle básico do ciclo de vida dos objetos reutilizáveis.
- **Context:** Fornece a implementação avançada através do `ApplicationContext`, gerenciando acesso à plataforma Java EE, propagação de eventos e recursos.
- **Expression Language (SpEL):** Define dinamicamente valores e comportamentos aos beans em tempo de execução via XML ou anotações.

#### Principais Subframeworks (Módulos):

- **Spring Boot:** Facilita a criação de aplicações independentes com servidores embutidos (como Tomcat) e configuração inicial mínima.
- **Spring Data:** Simplifica a interação com bancos de dados relacionais e não relacionais por meio de abstrações (ex.: Spring Data JPA e JDBC).
- **Spring Security:** Controla autenticação, autorização e proteção contra ataques.
- **Spring Batch:** Automatiza tarefas repetitivas e processamento de dados em lotes com tolerância a falhas.
- **Spring Cloud:** Suporta o desenvolvimento de microsserviços e computação em nuvem distribuída.
- **Spring AI:** Facilita a integração com os principais provedores de inteligência artificial generativa.

#### O Padrão DAO (Data Access Object) no Spring

O padrão **DAO** serve para abstrair e isolar o acesso físico aos dados da lógica de negócios.

- **Fluxo de Execução:** O **Usuário** envia uma requisição \(\rightarrow\) a interface **JSP** visualiza \(\rightarrow\) o **Controller** intercepta \(\rightarrow\) a camada de **Service** processa as regras de negócio e chama o **DAO** \(\rightarrow\) o **DAO** lê ou grava no **Banco de Dados** sem interferir nas regras ou transações de negócio.

---

### 3. Persistência de Dados com ORM Hibernate

O **Hibernate** é a principal implementação do padrão JPA no Java, responsável por mapear classes Java comuns (**POJOs**) diretamente para tabelas relacionais.

#### Arquitetura de Componentes do Hibernate:

1. **SessionFactory:** Configura as propriedades globais da aplicação e atua como fábrica de sessões de acesso ao banco.
2. **Session:** Representa a conexão física ativa com o banco de dados e gerencia o ciclo de vida e persistência das entidades Java.
3. **Transaction:** Interface usada pelo desenvolvedor para iniciar (`beginTransaction()`), confirmar (`commit()`) ou reverter (`rollback()`) operações atômicas críticas.
4. **JDBC e JPA:** O Hibernate utiliza a especificação JPA para padronização e se conecta fisicamente ao banco de dados por meio de drivers **JDBC**.

#### Mapeamento Prático de Entidades (Exemplo com Anotações):

```
@Entity // Indica que a classe representa uma tabela no banco de dados
@Table(name = "clientes") // Especifica o nome exato da tabela no banco
public class Cliente {
    @Id // Define o atributo como chave primária
    @GeneratedValue // Configura a geração automática do ID
    private Long id;

    @Column(name = "nome_cliente") // Opcional: especifica o nome da coluna
    private String nome;

    @OneToMany(mappedBy = "cliente") // Relacionamento de um para muitos
    private List<Pedido> pedidos;
}
```

#### Consultas e Otimização

- **HQL (Hibernate Query Language):** Linguagem orientada a objetos que realiza buscas baseadas nas **entidades e atributos** do código Java, e não nas tabelas físicas do banco. _Exemplo:_ `FROM Produto` em vez de `SELECT * FROM produtos`.
- **SQL Nativo:** Utilizado através do método `createNativeQuery()`. Garante controle total de performance e recursos específicos do banco de dados, mas **sacrifica a portabilidade** entre SGBDs.
- **Criteria API:** Permite construir consultas de forma programática e dinâmica em tempo de execução.

---

### 4. Desenvolvimento Mobile e Front-End

O desenvolvimento para dispositivos móveis exige controle rigoroso de recursos, processamento e memória.

#### Estrutura e Ciclo de Vida da Activity (Android)

No Android, uma **Activity** representa uma única tela de interface gráfica com a qual o usuário interage. Seu comportamento é ditado por um ciclo de vida estrito gerenciado pelo sistema operacional:

1. `onCreate()`: O ponto de entrada onde a tela é criada e a interface inicial é carregada.
2. `onStart()`: A Activity se torna visível para o usuário.
3. `onResume()`: A tela ganha o foco e entra em primeiro plano, pronta para interação.
4. `onPause()`: Outra Activity ganha o foco; o app é parcialmente interrompido.
5. `onStop()`: A tela deixa de estar visível para o usuário.
6. `onRestart()`: O usuário retorna para a Activity que estava em `onStop()`.
7. `onDestroy()`: A Activity é completamente destruída e liberada da memória.

_Preservação de Dados:_ Quando ocorrem interrupções (como rotação de tela ou queda de sinal), o estado do app deve ser salvo usando o mecanismo `onSaveInstanceState` e a arquitetura **ViewModel** para evitar perdas.

#### Comunicação entre Telas e Eventos

- **Intents:** Objetos usados para transportar dados e comandos entre diferentes telas. _Exemplo:_ Passar o nome de usuário autenticado da tela de login para a home (`Intent.putExtra`).
- **Listeners:** Registram cliques e interações (ex.: `setOnClickListener`), separando o comportamento visual da lógica de negócio.

#### Persistência Mobile Local vs. Remota

- **SQLite (Local):** Banco de dados relacional embutido de formato leve. Ideal para guardar preferências e permitir o **funcionamento offline** do aplicativo.
- **Web Services (Remoto):** Comunicação realizada com servidores externos via HTTP/REST utilizando formatos como **JSON**. Bibliotecas como o **Retrofit** com funções assíncronas de Kotlin (_Coroutines_) evitam que as chamadas de rede bloqueiem a tela do celular.

---

### 5. Tecnologias de Visualização e Back-End (Java EE, JS, PHP, Python)

A arquitetura de sistemas modernos divide as responsabilidades em camadas específicas para garantir a manutenibilidade.

#### Tecnologias Java EE (Jakarta EE) corporativas:

- **JSP (JavaServer Pages):** Tecnologia de front-end baseada em arquivos HTML com código Java embutido para gerar páginas dinamicamente.
- **Tag Libraries (JSTL):** Coleções de tags customizadas (como `<c:forEach>` e `<c:if>`) que eliminam a necessidade de escrever código Java nativo nas JSPs, tornando o código limpo.
- **Servlets:** Componentes controladores (Controller no padrão MVC) que intermedeiam as requisições HTTP entre o front-end e o back-end.
- **Session Beans:** Componentes EJB focados na lógica de negócios.

#### Frameworks JavaScript:

- **Angular:** Framework estruturado e completo (desenvolvido pelo Google) baseado em TypeScript, focado em aplicações de página única (SPA).
- **React.js:** Biblioteca (frequentemente usada como framework) focada no desenvolvimento de interfaces reativas utilizando **Virtual DOM** para otimizar o desempenho.
- **Vue.js:** Framework progressivo de curva de aprendizado suave que combina características do React e do Angular com vinculação bidirecional de dados.
- **Node.js (Back-End):** Ambiente de execução que roda JavaScript no lado do servidor com uma arquitetura **assíncrona e orientada a eventos (Event-Driven)**, ideal para aplicações em tempo real. O **Express.js** é seu framework mais minimalista e popular para APIs.

#### Frameworks PHP:

- **Laravel:** Focado em produtividade máxima, sintaxe elegante, utilizando o **Eloquent ORM** e motor de templates Blade.
- **Symfony:** Framework robusto voltado a projetos empresariais sob medida, altamente modular e baseado no **Doctrine ORM**.
- **CodeIgniter:** Solução minimalista de extrema leveza e baixa curva de aprendizado, ideal para projetos menores.
- **Zend Framework (Laminas):** Altamente corporativo, extensível, baseado em padrões PSR de segurança e conformidade.

#### Frameworks Python:

- **Django:** Framework completo ("batteries included") baseado na arquitetura **MTV** (Model-Template-View). Traz recursos integrados nativos como ORM, autenticação, rotas e painel administrativo.
- **Flask:** Microframework minimalista, flexível e leve, dando total liberdade arquitetural para o desenvolvedor compor apenas as bibliotecas necessárias.

---

## Conceitos que não posso confundir

|Conceito A|Conceito B|Diferença Crucial|
|:--|:--|:--|
|**Framework**|**Biblioteca**|Na biblioteca, o programador chama o código da biblioteca quando quer. No framework, o controle se inverte: é o framework que chama o código do programador dentro de uma estrutura preestabelecida.|
|**HQL**|**SQL Nativo**|O HQL opera sobre as classes Java (entidades) e seus atributos. O SQL Nativo opera diretamente sobre as tabelas e colunas físicas do banco de dados.|
|**Inversão de Controle (IoC)**|**Injeção de Dependências (DI)**|A IoC é um conceito de design geral (transferir o controle de fluxo para o framework). A DI é a aplicação prática e específica desse conceito voltada a fornecer as instâncias das classes dependentes.|
|**Stateless Session Bean**|**Stateful Session Bean**|Os beans Stateless não guardam nenhum estado de conversação com o cliente. Os beans Stateful mantêm o estado e as informações conversacionais ativas enquanto durar a sessão do cliente.|
|**Framework Completo**|**Microframework**|O completo (ex.: Django) entrega todas as ferramentas integradas por padrão (ORM, autenticação, admin). O micro (ex.: Flask) fornece o mínimo para rodar a aplicação, permitindo que você decida quais módulos externos instalar.|
|**JPA**|**Hibernate**|JPA é uma especificação conceitual de padronização (a regra de persistência). Hibernate é a ferramenta de software real que implementa e executa fisicamente as diretrizes da JPA.|
|**Eloquent ORM**|**Doctrine ORM**|O Eloquent (Laravel) mapeia dados de forma direta e fluida nas classes ativas. O Doctrine (Symfony) utiliza uma separação mais rígida e formal (Data Mapper) entre as entidades e o gerenciador de persistência.|
|**Ajax**|**Angular**|Ajax é uma técnica JavaScript de requisições assíncronas isoladas (não é um framework). Angular é um framework estrutural completo para desenvolvimento de aplicações SPA complexas.|

---

## Pontos importantes para prova

1. **Ordem do Fluxo da Arquitetura MVC do Spring:**
    - `Navegador do Usuário` envia requisição \(\rightarrow\) `Front Controller` (Servlet do Spring) intercepta \(\rightarrow\) Repassa ao `Controller` do desenvolvedor \(\rightarrow\) Encaminha para o `View Template` (página HTML/JSP) \(\rightarrow\) Retorna o resultado renderizado ao usuário.
2. **O Problema do N+1 Queries no Hibernate:**
    - **O que é:** Ocorre quando a aplicação executa uma consulta inicial para obter uma lista de registros e depois dispara uma consulta adicional para cada registro de forma individualizada para trazer dados relacionados, causando gargalos e sobrecarga no banco.
    - **Como evitar:** Mitiga-se configurando carregamentos estratégicos (**Fetch Joins**) e mapeamentos inteligentes com a anotação `@Fetch`.
3. **Configuração de Criação Automática do Banco no Hibernate:**
    - Controlada pela propriedade `hibernate.hbm2ddl.auto` no arquivo de configuração XML (`update` ou `create`). **Cuidado:** Deve ser evitada ou usada com extrema disciplina em ambientes de produção.
4. **Transações e Segurança:**
    - As operações de escrita no banco de dados devem estar obrigatoriamente protegidas por transações (uso de `@Transactional` ou APIs de `Transaction`) para garantir a atomicidade (**ou tudo ocorre com sucesso, ou tudo é revertido via rollback**).
    - A parametrização de consultas (ex.: parâmetros nomeados `:param` no HQL) é uma **regra de segurança obrigatória** para evitar ataques de injeção de SQL (_SQL Injection_).
5. **Classificação de Componentes:**
    - _Interface de Usuário:_ Botões, caixas de texto e janelas.
    - _Serviço:_ Acesso a banco de dados, mensagens e integrações.
    - _Domínio:_ Representação das regras de domínio (difícil reutilização).

---

## Revisão rápida

- **Frameworks** ditam a estrutura; **bibliotecas** são chamadas pelo seu código.
- **IoC** delega o fluxo; **DI** fornece os componentes (beans) automaticamente.
- **Componentes básicos do Spring:** Core, Beans, Context, SpEL.
- **Arquitetura Hibernate:** SessionFactory (fábrica de sessões), Session (conexão ativa) e Transaction (controle atômico).
- **HQL** foca em classes/atributos; **SQL Nativo** foca em tabelas/colunas (perde portabilidade).
- **Ciclo de vida Android (7 etapas):** onCreate \(\rightarrow\) onStart \(\rightarrow\) onResume \(\rightarrow\) (interrupção) \(\rightarrow\) onPause \(\rightarrow\) onStop \(\rightarrow\) onRestart \(\rightarrow\) onDestroy.
- **SQLite** para persistência estruturada offline local; **Web Services (Retrofit + JSON)** para sincronização de dados remotos online.
- **JSP + JSTL** no front-end Java EE separam regras visuais de códigos Java puros.
- **Node.js** roda JavaScript no back-end de forma assíncrona, rápida e sem bloqueios de I/O.
- **Laravel (PHP)** usa Eloquent ORM; **Symfony (PHP)** usa Doctrine ORM.
- **Django (Python)** é robusto e completo (MTV); **Flask (Python)** é micro, leve e flexível.

---
