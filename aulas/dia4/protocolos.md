# O que é um serviço WEB?

# Protocolos

Protocolo é um acordo, um padrão que define regras para comunicação entre sistemas

Um exemplo é que quando criança brincamos de telefone sem fio, onde definimos um protocolo com nossos amigos que é falar susurrando para então outros amigos passarem essa mensagem a frente.

HTTP - HyperText Transfer Protocol - é um protocolo que define regras para transferencia de documentos

FTP - File Transfer Protocol - é um protocolo que define regras para transferencia de arquivos

SMTP - Simple Mail Transfer Protocol - é um protocolo que define regras para transferencia de emails

Nem toda informação enviada na internet, chega 100% completa, como por exemplo o TCP que possui um sistema de Error Recovery que identifica quando um pacote não chega e pede para que seja reenviado.

Um protocolo consegue ser montado um em cima do outro, como por exemplo o HTTP que define como as informações web vão ser trocadadas e podem ser enviadas pelo protocolo TCP, e para transitar os dados entre os "tuneis" que conectam a internet é utilizado o protocolo Internet Protocol (IP).

Mas não necessariamente precisamos utilizar mandatoriamente o TCP pois a garantia que ele tras em relação a entrega dos pacotes tem um custo, e existem casos que não precisamos dessa garantia, como por exemplo em apps de reunião como zoom, skype, discord etc onde não importa se um frame se perdeu no caminho.

Nesse cenário podemos utilizar o UDP (User Datagram Protocol) que não garante a entrega dos pacotes. Datagram significa um pedaço de informação autocontido onde cada pacote é auto-suficiente e não depende de uma conferência entre os dois lados.

Vídeo UDP vs TCP: https://www.youtube.com/watch?v=ZEEBsq3eQmg
