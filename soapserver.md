Para criar um servidor SOAP simples usando Java, vamos utilizar a biblioteca Apache CXF. É importante ressaltar que, para implementar um servidor SOAP, é necessário definir o contrato do serviço, ou seja, a interface que será implementada pelo servidor e exposta aos clientes.

Neste exemplo, vamos criar uma interface chamada ExemploService, que terá quatro métodos: somar, subtrair, multiplicar e dividir. Esses métodos irão receber dois números inteiros como parâmetro e retornar o resultado da operação.

Adicione as dependências do Apache CXF e do Jetty no arquivo pom.xml:

<dependencies>
  <dependency>
    <groupId>org.apache.cxf</groupId>
    <artifactId>cxf-rt-frontend-jaxws</artifactId>
    <version>3.4.6</version>
  </dependency>
  <dependency>
    <groupId>org.eclipse.jetty</groupId>
    <artifactId>jetty-server</artifactId>
    <version>11.0.6</version>
  </dependency>
</dependencies>


Crie a interface ExemploService:

package com.example;

import javax.jws.WebMethod;
import javax.jws.WebParam;
import javax.jws.WebService;

@WebService
public interface ExemploService {

    @WebMethod
    int somar(@WebParam(name = "a") int a, @WebParam(name = "b") int b);

    @WebMethod
    int subtrair(@WebParam(name = "a") int a, @WebParam(name = "b") int b);

    @WebMethod
    int multiplicar(@WebParam(name = "a") int a, @WebParam(name = "b") int b);

    @WebMethod
    int dividir(@WebParam(name = "a") int a, @WebParam(name = "b") int b);

}

Crie a classe ExemploServiceImpl, que implementa a interface ExemploService:

package com.example;

import javax.jws.WebService;

@WebService(endpointInterface = "com.example.ExemploService")
public class ExemploServiceImpl implements ExemploService {

    @Override
    public int somar(int a, int b) {
        return a + b;
    }

    @Override
    public int subtrair(int a, int b) {
        return a - b;
    }

    @Override
    public int multiplicar(int a, int b) {
        return a * b;
    }

    @Override
    public int dividir(int a, int b) {
        if (b == 0) {
            throw new ArithmeticException("Divisão por zero");
        }
        return a / b;
    }

}

Crie a classe ServidorSoap:

package com.example;

import org.apache.cxf.jaxws.JaxWsServerFactoryBean;

public class ServidorSoap {

    public static void main(String[] args) {
        JaxWsServerFactoryBean factory = new JaxWsServerFactoryBean();
        factory.setServiceClass(ExemploService.class);
        factory.setAddress("http://localhost:8080/exemplo");
        factory.setServiceBean(new ExemploServiceImpl());
        factory.create();
    }

}

Execute a classe ServidorSoap. O servidor SOAP estará rodando na porta 8080.
Agora, é possível acessar o serviço utilizando as operações definidas na interface ExemploService.