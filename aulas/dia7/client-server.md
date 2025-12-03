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

Agora é possível utilizar servidores externos, que possuem tratamento para todas essas possibilidades de queda de energia, internet e são mais potentes para aguentar diferentes acessos simultâneos

### Continuous Deployment

Automatização do Deploy
