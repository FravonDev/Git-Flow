<h1>GIT Flow</h1>

Usar Git Flow é importante pois ajuda a manter o controle e organização do código, facilita trabalhar em equipe, facilita o lançamento e melhora a qualidade do projeto. Tudo isso é essencial para o sucesso do projeto.

Dependendo do tamanho do projeto podemos usar 2 tipos de flow, o simplificado e o 

# Flow Simplificado

Em projetos que terão apenas 1 desenvolvedor trabalhando no projeto, pode ser legal utilizar um fluxo simplificado

![flow simplificado](https://media.discordapp.net/attachments/1063854443524796476/1063856067882274956/imagem_2023-01-14_125130427-removebg-preview_1.png)

para projetos maiores, com mais desenvolvedores, utilizamos uma estrutura mais complexa, para manter tudo organizado

# GIT FLOW

![flow normal](https://media.discordapp.net/attachments/1063854443524796476/1063855668878135386/imagem_2023-01-14_124749040-removebg-preview.png)

 ele sugere que rotulemos a master, na primeira versão é a **V1.0**

Os próximos updates são:  **V1.1** , **V1.2** e **V1.3 …**

# Como é o fluxo?

1. A branch **master** é protegida, ou seja, ninguém trabalha diretamente nela. Ela só deve ser atualizada quando uma nova versão estável do projeto estiver pronta para ser lançada
2. Trabalhamos, ou seja, desenvolvemos esse fluxo na branch **develop**
3. Quando você quiser desenvolver uma nova funcionalidade, crie uma nova branch com um nome legal, como **feature_nomelegal**  Nessa branch, você vai desenvolver a nova funcionalidade.
4. Quando terminar de desenvolver a funcionalidade, envie para a branch **develop.**
5. Quando todas as funcionalidades estiverem prontas e houver um entregável, mande-o para a branch **releas**. Nessa branch, o QA e o cliente vão validar se está tudo certo antes do lançamento.
6. Se precisar fazer algum **FIX** na documentação e coisas do tipo, pra isso volte a branch **develop** e se precisar criar uma nova funcionalidade quando tiver fazendo esse **FIX,** crie uma branch para feature.
7. Quando **TUDO** estiver **PERFEITAMENTE TESTADO** **e APROVADO**, é hora de mandar para a branch **master**! Nessa branch, só entra o que está pronto para ser lançado para o mundo, ou seja, a versão mais nova e estável do seu projeto. E aí, é só dar uma boa tag nela, como **V1.1**, **V1.2**, e assim por diante.
8. O **hotfix** é criado a partir da branch **master**, ao invés de **feature**. O hotfix é usado para correções urgentes e críticas, quando houver algum problema crítico na branch master, você criará uma nova branch hotfix a partir da master, fará as correções necessárias e depois enviará essa branch de volta para a master. E também é boa prática dar uma tag nessa nova versão

## Usando gitflow

precisamos instalar, no windows se já tem o git instalado, já tem gitflow. 

Para inicializar usamos o comando

```jsx
git flow init
```

É comum ver repositórios poluídos com varias branchs que não deveriam mais existir

as branches de suporte serão automaticamente excluídas

podemos nomear nossa branchs de suporte.

podemos adicionar prefixos na “Version tag prefix”

após criar já estaremos na branch develop.

 Podemos ver a estrutura inicial sa 

```jsx
git branch
```

**Funcionalidade**

Vamos trabalhar em uma funcionalidade **sum**, pra isso vamos criar uma branch para feature com o gitflow:

```jsx
git flow feature start sum
```

Quando terminarmos de trabalhar nessa branch usamos

```jsx
$ git add .
$ git commit -m "sum funcionality"
```

Depois que colocarmos as modificações em stage, usamos:

```jsx
git flow feature finish sum
```

com isso ele vai fazer o merge na nossa **develop/sum** automagicamente 

se temos um **entregável** com todas as funcionalidades e quisermos entregar, ou seja, criar a release.

é bem parecido com criar a feature, é recomendado nomear as tags de forma semântica

```jsx
git flow release start 0.1.0
```

Nesta etapa a nossa **release** será testada, se for aprovada, vamos fechar a release igual

```jsx
git flow release finish 0.1.0 -m "Versão inicial da release"
```

Quando fizermos isso, ele vai pedir uma mensagem de **merge**

Basta apertar **ESC** no terminal, depois 

```jsx
:wq!
```

ele vai pegar o nome da release que **nesse caso** era: 0.1.0 e vai usar na tag

se eu criar um **HOTFIX** ele vai atualizar a **master** e também irá atualizar a **develop**

Se tiver alguma alteração na **release** ela atualiza a master e também atualiza a **develop** automagicamente