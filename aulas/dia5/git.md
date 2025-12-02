# Git

O git é um sistema de controle de versão DISTRIBUIDO.
Ele tem esse nome pois antigamente o controle de versão era feito através de um unico servidor/máquina centralizado, onde ficavam renomeando a pasta do projeto para atualizar e diferenciar as versões: projeto-v1, projeto-v2...

# Linha do Tempo

O sistema de controle de versão passou por uma linha temporal até chegar no Git:

Centralizados

- 1972: SCCS (Source Code Control System)
- 1982: RCS (Revision Control System)
- 1983: CVS (Concurrent Versions System)
- 2000: SVN (Subversion)

---

Distribuídos

- 2005: Git (Git)

## Sistemas Centralizados

Em um sistema de controle de versão Centralizado os arquivos ficam em um servidor e funcionam como um hotel, os desenvolvedores "Alugam" determinados arquivos realizando um checkout. Quando feito esse checkout os arquivos ficam indisponíveis para edição de outras pessoas, permitindo apenas a leitura, e quando o desenvolvedor termina de alterar esse arquivo ele realiza um checkin, aonde essa nova versão do arquivo fica disponível no servidor (hotel).

Todo esse sistema é utilizado para evitar o maior vilão de toda história do versionamento. O MERGE, a mescla, a junção de alteraçoes de diversas pessoas em um mesmo arquivo. Porém esse método acaba travando o fluxo de trabalho, já que existe uma espera até que seja feito o checkin daquele arquivo para outras modificações.

## Sistemas Distribuidos

Já os sistemas Distribuidos, permitem que cada usuário faça uma cópia (CLONE) daquele projeto localmente, permitindo que ele manipule os arquivos da maneira que quiser, além disso existe um algoritmo que quando identifica alterações no mesmo arquivo e consegue disponibilizar ferramentas visuais e a possibilidade de realizar o merge de forma segura, aproveitando alterações de ambos os lados. O nome desse processo se chama **Merge Conflict** e é acionado quando existe alterações de duas partes no mesmo trecho de código.

Lembrando que todo esse processo de resolução de conflitos é feito localmente, dessa forma, toda alteração só vai para o repositório de referência caso seja o processo de commit e push.

## Diff

Diff
O Diff é uma ferramenta que permite a comparação de duas fontes diferentes de código. Nos sistemas de versionamento mais antigos como o CVS e SVN, era criada uma linha do tempo das modificações e o diff (também chamado de Delta Encoding) salvava apenas o que foi modificado, e não as duas versões do arquivo.
Salvando Diffs (Delta Storage)
Como funciona:

Você salva uma versão completa inicial
Cada mudança posterior salva apenas o que mudou

```
Exemplo:
Versão 1: "Olá mundo"           [arquivo completo]
Versão 2: "Olá mundo feliz"     [+" feliz"]
Versão 3: "Oi mundo feliz"      ["Olá" → "Oi"]
```

Vantagens: Economiza espaço em disco
Desvantagens: Lento para acessar versões antigas (precisa reconstruir todo o histórico) e vulnerável a corrupção (se perde um delta, perde tudo depois dele)

Snapshots (Método Git)
Snapshot (ou "fotografia") é uma abordagem de versionamento onde o sistema salva o estado completo do projeto em cada ponto no tempo, como se tirasse uma foto de todos os arquivos naquele momento. Em vez de registrar "o que mudou", registra "como está tudo agora".

Salvando Snapshots (Git)
Como funciona:

Cada commit salva o estado completo de todos os arquivos modificados
Arquivos não modificados apenas referenciam o blob anterior (sem duplicação)

```
Exemplo:
Commit 1: arquivo.txt = "Olá mundo"        [conteúdo completo]
Commit 2: arquivo.txt = "Olá mundo feliz"  [conteúdo completo]
Commit 3: arquivo.txt = "Oi mundo feliz"   [conteúdo completo]
```

## Funcionamento do Git

Quando inicializamos o arquivo .git, nós tiramos uma foto do repositório, dessa forma cada arquivo recebe um identificador e é salvo dentro do .git aonde esse pacote contendo o identificador e conteudo do arquivo se torna um objeto chamado **Blob** ou Binary Large OBject. E quando alteramos esses arquivos gerando uma nova foto, o git cria um NOVO objeto Blob, contendo todo conteúdo + alterações daquele arquivo, assim mantendo um histórico de alterações. Obs: Os arquivos que não foram alterados não possuem um Blob novo.

Essa **foto** que estamos falando possuí o nome de **COMMIT** que traduzindo significa Compromisso, ou seja, nós autores desse commit (foto) estamos comprometidos com essas alterações que foram realizadas.

Podemos ver essas "fotos" através do comando **git log** que retornará algo parecido com isso:

```
commit 78507bf202f4bf23390957473c8e84eb3b9079c9
Author: Daniel Manoel <danielmanoelfilho44@gmail.com>
Date:   Mon Dec 1 17:33:53 2025 -0300
✨ init repo
```

É possível uma grande cadeia de caracteres, esse é o identificador único dessa foto (commit)

E quando precisamos ver essas alterações, o git aponta um blob contra o outro, ou seja UMA FOTO CONTRA A OUTRA, e ai podemos ver as diferenças entre as versões, parecido com um jogo dos 7 erros :D

## Os 3 Estágios do versionamento

### Modified (Modificado)

O primeiro estagio acontece quando um arquivo já conhecido pelo .git (Ou seja, que já possuí uma foto) sofre uma alteração ele fica marcado como **Modified**

### Staged (Preparado)

Vamos supor que você está caçando um bug, e modificou diversos arquivos, e quando resolveu o bug, precisou mexer em apenas um arquivo. Nesse estágio de preparo, é possível dizer ao git que você só quer considerar as alterações realizadas naquele arquivo específico, e então consegue voltar os outros arquivo para versão original.

### Commit

Nesse estágio é onde você irá tirar a nova foto daquele arquivo que foi modificado, separado e por fim vai ser COMMITADO, para que a alteração permaneça.

### Untracked

Eu sei que escrevi apenas 3 ESTÁGIOS e realmente são, pois essa condição acontece quando o GIT não conhece os arquivos que estão no repositório, ou seja, eles não possuem uma snapshot, são arquivos novos que não fazem parte do fluxo do git (git flow)

---

Pensando no último estágio onde temos arquivos não rastreados, existe uma situação onde não queremos subir pastas ou arquivos específicos para o nosso repositório, como por exemplo as pastas que possuem dependências como "node_modules" ou ".next".

Mas por que não subir essas dependências para o repositório sendo que são necessárias para o funcionamento do projeto?

Isso acontece pois esses arquivos fazem parte do processo de build, e cada ambiente tem que fazer esse build, portanto são arquivos dinâmicos que não precisam subir para o repositório. E uma situação de deploy (produção) esses arquivos são gerados de forma até MAIS otimizada, onde eles ficam mais leves e compactados do que em um ambiente de desenvolvimento (máquina local)

Porém, mesmo não subindo ao repositório, esses arquivos são de extrema importância para rodar o projeto localmente, para isso podemos utilizar o: **.gitignore**

## .gitignore

Nesse arquivo podemos colocar o nome ou caminho de pastas e arquivos, que queremos manter no nosso ambiente local, mas não subir ele para o repositório git.

Sabendo que não

---

Obs Gerais:

Logs -> Registros
Vlogs -> Registros em Vídeos
