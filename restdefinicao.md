As seis regras de uma API REST são conhecidas como Restful Constraints ou Princípios REST, e foram definidas por Roy T. Fielding em sua tese de doutorado. São elas:

Arquitetura cliente-servidor: A separação entre a interface do usuário e o armazenamento de dados, permitindo que ambas as partes evoluam de forma independente.

Comunicação stateless: Cada requisição do cliente para o servidor deve conter todas as informações necessárias para que o servidor possa compreendê-la, sem depender de informações de requisições anteriores.

Cache: O servidor deve definir quais respostas podem ser cacheadas ou não, e o cliente deve respeitar as informações de cache recebidas.

Interface uniforme: A API deve seguir uma interface uniforme para todas as requisições. Isso inclui a utilização de recursos, que são identificados por URLs, e os métodos HTTP, que indicam a ação a ser realizada nos recursos.

Camadas: A arquitetura deve permitir a utilização de camadas intermediárias entre o cliente e o servidor, como proxies e gateways, melhorando a escalabilidade do sistema.

Sistema de código sob demanda (opcional): O servidor pode enviar código executável ao cliente para ser executado em sua máquina, estendendo as funcionalidades da aplicação. Essa regra é opcional e raramente utilizada em APIs REST.

Essas regras são fundamentais para a construção de uma API REST bem estruturada, que seja fácil de utilizar e evoluir, além de ser mais escalável e confiável.