# DNS

Como definição DNS (Domain Name System) é um sistema de nomes de domínio que permite que os usuários acessem sites usando nomes de domínio em vez de endereços IP.

Porém, domínios são uma MENTIRA, pois google.com, youtube.com etc... não são endereços de verdade, são apelidos. Os verdadeiros endereços na internet são os IPs (Internet Protocol)

O domínio é a forma como nós usuários acessamos os sites e serviços pela internet, mas para o computador ele sempre utiliza o endereço de IP.

E como o computador sabe o endereço de IP de destino que ele está tentando acessar?

Uma boa analogia é pensar que o sistema de DNS funciona como um banco de dados, onde o fluxo é o seguinte: O computador tenta acessar o youtube.com, então é enviado um requisição ao SERVIDOR DNS, que vai verificar na tabela de banco de dados qual é o IP relacionado ao domínio youtube.com.

# Aula 2 DNS

Vamos entender mais a fundo o relacionamento para que o computador consiga encontrar o endereço de IP correto.

Inicialmente, antes de chegar ao servidor DNS do site que você deseja acessar, o seu computador faz uma busca pelo endereço no Recursive Resolver, que se encontra no provedor de internet, esse cara é o responsável por encontrar e resolver o nosso endereço de IP.

Ele faz isso através da lista de Root Servers, que são servidores que contém informações sobre os domínios principais da internet e que atualmente possuí 1959 instâncias espalhadas pelo planeta, para garantir a redundância e integridade do serviço.

Quando o Recursive Resolver pergunta ao Root Server qual é esse endereço de IP, porém ele responde que **NÃO SABE**. (PLOT TWIST).

MAAAS, o Root Server sabe ler o domínio ao contrário ou seja: br.com.youtube pois ele sabe quem toma conta dos domínios .br

Uma coisa curiosa sobre os domínios é que quando ao contrário eles não começam com **br** mas sim com **.** (youtube.com.br.). Isso se chama Fully Qualified Domain Name (SQDN) - Nome de Domínio Completamente Qualificado, sendo assim esse é o endereço completo e a busca começa a partir do **.** que representa o **root domain**.

A segunda parte, que é o **br** significa TLD (Top-Level Domain) e essa informação é única coisa que os Root Servers conhece e conseguem encontrar.

A lista de TLDs é imensa, mas são separadas em duas grandes categorias:

- ccTLDs (Country Code Top-Level Domain) - Domínios de País;
- gTLDs (Generic Top-Level Domain) - Domínios Genéricos;

Voltando ao fluxo, após o Root Server encontrar qual o TLD relacionado a busca do Recursive Resolver, ele envia uma nova lista de servidores que fazem parte do domínio do TLD.

E então o Recursive Resolver pergunta para um desses servidores que possuém o TLD .br qual o IP final do domínio youtube.com.br.

Então o servidor .br retorna um outro IP que é do Authoritative Server que é o servidor que possúi todos os registros do seu domínio, e então ele devolve o endereço final
