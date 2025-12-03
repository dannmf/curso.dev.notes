# Client Server

A relação de cliente servidor tem como principio principal o **Client** pedir algo e o **Server** responder.

Ex: O filho na hora do almoço pede para o pai lhe passar um copo que esta sobre a mesa, o pai então pega o copo e entrega ao menino.

Nesse exemplo o filho é o **Client** e o pai é o **Server**.

Em um outro exemplo colocando mais um ator: Em um restaurante o você pede ao garçom um prato, o garçom então vai até a cozinha e passa esse pedido para que os cozinheiros possam preparar o prato. Após preparado a cozinha entrega o prato ao garçom, que finaliza o processo entregando o prato ao cliente.

Nesse exemplo você v é o client, pedindo o prato ao garçom. O garçom por sua vez é o server que recebe o pedido, porém o garçom se coloca no papel de Client, pois precisa passar o pedido para a cozinha, que é o SERVER

## Deploy

Realizar o deploy é implantar o sistema.

Antigamente utilizavamos uma máquina como servidor, para fornecer a nossa aplicação na internet, porém caso caisse a energia ou acontecesse algum tipo de problema com o computador, a aplicação parava de funcionar.

Depois surgiram os servidores, onde tinhamos que passar nossos arquivos a ele via protocolo FTP. O servidor então disponibilizava todo tratamento para problemas de energia e internet e também era mais potente para acessos simultâneos, porém na hora de atualizar tinha que tomar cuidado para selecionar apenas os arquivos que foram alterados. Isso fazia com que o processo fosse EXTREMAMENTE manual

E como estava dando muito trabalho passar os arquivos da máquina para o servidor, resolveram então editar diretamente no servidor EM AMBIENTE DE PRODUÇÃO :D (que ótima idéia) eles se conectavam via Windows Server ou SSH para editar diretamente no servidor.

Com a vinda do GIT, isso ficou naturalmente mais simples e descentralizado, pois agora é possível utilizar o GIT também no servidor, aonde basta acessar o servidor e puxar as alterações de origem utilizando o git pull.

Mas ainda sim, mexer diretamente no servidor pode não ser uma boa idéia e para resolver isso, agora no processo de deploy é utilizado várias máquinas até o servidor de produção

Então antes de chegar no servidor de produção o projeto passara por um servidor C.I (Continuous Integration) que irá realizar diversos testes para que checar se tudo está funcionando, após isso passará por um servidor de build/CD (Continuous Deployment), que vai pegar o código fonte, otimizar e construir o projeto final e por fim irá para o servidor de produção que vai estar exposto na internet.

### Continuous Deployment

Automatização do Deploy
