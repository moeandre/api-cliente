FORMAT: 1A
HOST: http://www.mowaservices.com.br/

# TOKIO API
 Tokio Marine API documentation

# Group Login
The Login Resource

## Login [/rest/login]

Validates the user access in the system

### POST

User access using username and password

+ Request (application/x-www-form-urlencoded)

    + Parameters
        + login (string) ... the username .
        + senha (string) ... the password .

    + Body
    
        ```
        [
        "login" : "123.123.123-45", 
        "senha" : "password" 
        ]
        ```

+ Response 200 (application/json)

    ```js
    {
        "success": true 
    }
    ```

## Login Social [/rest/login/social] 

Validates the user access in the system

### POST

User access using social credentials

+ Request (application/x-www-form-urlencoded)

    + Parameters
        + idProvider (string) ... the provider ID of the account. Could be 'facebook' or 'twitter' .
        + idSocial (string) ... the social ID of the user.

    + Body
    
        ```
        [
        "idProvider" : "facebook",
        "idSocial" : "43175098" 
        ]
        ```

+ Response 200 (application/json)

    ```js
    {
        "success": true 
    }
    ```

# Group Usuario
The Usuario Resource

## User Activate [/rest/usuario/primeiroacesso]

Activate user with username and password

### POST

Do login using username and password

+ Request (application/x-www-form-urlencoded)

    + Parameters
        + cpfCnpj (String) ... cpf/cnpj number
        + apolice: (String)  ... apolice number 
        + email: (String) ... email address
        + confirmacaoEmail: (String) ... email address confirmation
        + celular: (String) ... cellphone number 
        + confirmacaoCelular: (String) ... cellphone number confirmation

    + Body
    
        ```
        [
        "cpfCnpj" : "123.123.123-60",
        "apolice" : "123456",
        "email" : "mail@mail.com",
        "confirmacaoEmail" : "mail@mail.com",
        "celular" : "(11)99999-8888",
        "confirmacaoCelular" : "(11)99999-8888"
        ]
        ```

+ Response 200 (application/json)

    ```js
    {
        "success": true,
        "message": "Cadastro Realizado com sucesso! Uma mensagem com as informações e instruções de acesso será encaminhada para o endereço de e-mail informado {email}" 
    }
    ```

## Password Recovery [/rest/usuario/recuperarSenha]

Reset the lost password of a given user

### POST

Recovery lost password of the user

+ Request (application/x-www-form-urlencoded)

    + Parameters
        + cpfCnpj (String) ... cpf/cnpj number

    + Body
    
        ```
        [
        "cpfCnpj" : "123.123.123-60"
        ]
        ```

+ Response 200 (application/json)

    ```js
    {
        "success": true,
        "message": "Uma mensagem com as informações e instruções de acesso será encaminhada para o endereço de e-mail email@email.com"
    }
    ```

## Social User Activate [/rest/usuario/social]

Activate social user with Social Token ID

### POST

Activate user with social credentials

+ Request (application/x-www-form-urlencoded)

    + Parameters
        + cpfCnpj (String) ... cpf/cnpj number
        + apolice: (String)  ... apolice number 
        + email: (String) ... email address
        + confirmacaoEmail: (String) ... email address confirmation
        + celular: (String) ... cellphone number 
        + confirmacaoCelular: (String) ... cellphone number confirmation
        + idProvider (string) ... the provider ID of the account. Could be 'facebook' or 'twitter' .
        + idSocial (string) ... the social ID of the user.

    + Body
    
        ```
        [
        "cpfCnpj" : "123.123.123-60",
        "apolice" : "123456",
        "email" : "mail@mail.com",
        "confirmacaoEmail" : "mail@mail.com",
        "celular" : "(11)99999-8888",
        "confirmacaoCelular" : "(11)99999-8888",
        "idProvider" : "facebook", 
        "idSocial" : "43175098"
        ]
        ```

+ Response 200 (application/json)

    ```js
    {
        "success": true
    }
    ```

# Group Apolice

The Apolice Resource

## List all Insurance Policies [/rest/apolice/listar]

List all Insurance Policies of a given User

### POST

List all Insurance Apolicies of a given User

+ Request (application/x-www-form-urlencoded)

    + Parameters
        + cpf ( required , string , `123.123.123-12`) ...  cpf number

    + Body
    
        ```
        [
        "cpf" : "123.123.123-12"
        ]
        ```

+ Response 200 (application/json)

    ```js
    {
        "apolices" :
        [
            {
                 "produto": "produto" ,
                 "apolice": "apolice", 
                 "situacao": "situacao",
                 "idepol": 123456,
                 "numcert": 123456,
                 "numoper": 123456
             }
        ],
        "success": "true",
        "errorMessage" : "Nenhuma apolice encontrada." 
    }
    ```

## Get Insurance Policy [/rest/apolice/detalhar]

Get Insurance Policy`s details

### POST

Get Insurance Apolicy`s details

+ Request (application/x-www-form-urlencoded)

    + Parameters
        + idepol ( required , long , 123456) ... idepol 
        + numcert ( required , long , 123456) ... numcert
        + numoper ( required , long , 123456) ... numoper

    + Body
    
        ```
        [
        "idepol" : 123456,
        "numcert" : 123456,
        "numoper" : 123456
        ]
        ```

+ Response 200 (application/json)

    ```js
    {
        "success": "true", 
        "apolice" :
            {
                "fabricante": "fabricante",
                "modelo": "modelo",
                "frase", "frase",
                "anoFabricacao": 2013,
                "anoModelo": 2013,
                "tipoCategoria": "tipoCategoria",
                "placa": "ABC-1234",
                "veiculoZeroKm":true
            },
        "errorMessage" : "Apolice não encontrada."
    }
    ```

## List Covered Risks [/rest/apolice/coberturas]

List Covered Risks of a given Insurance Policy

### POST

List Covered Risks of a given Insurance Policy

+ Request (application/x-www-form-urlencoded)

    + Parameters
        + idepol ( required , long , 123456) ...  idepol 
        + numcert ( required , long , 123456) ... numcert
        + numoper ( required , long , 123456) ... numoper

    + Body
    
        ```
        [
        "idepol" : 123456,
        "numcert" : 123456,
        "numoper" : 123456
        ]
        ```

+ Response 200 (application/json)

    ```js
    {
        "coberturas" :
        [
            "descricaoCobertura" : "valorCobertura"
        ],
        "mensagens" : "mensagensDiversas",
        "success": true,
        "errorMessage" : "Nenhuma cobertura encontrada."
    }
    ```

## List Services [/rest/apolice/servicos]

List Services of a given Insurance Policy 

### POST

List Services of a given Insurance Policy 

+ Request (application/x-www-form-urlencoded)

    + Parameters
        + idepol ( required , long , 123456) ...  idepol 
        + numcert ( required , long , 123456) ... numcert
        + numoper ( required , long , 123456) ... numoper

    + Body
    
        ```
        [
        "idepol" : 123456,
        "numcert" : 123456,
        "numoper" : 123456
        ]
        ```

+ Response 200 (application/json)

    ```js
    {
        "success": "true", 
        "servicos" :
        [
            { 
                "nomeServico" : "descricaoServico"
            }
        ],
        "errorMessage" : "Nenhum serviço encontrado."
    }
    ```

## List All Installments [/rest/apolice/parcelas]

List All Installments of a given Insurance Policy

### POST

List All Installments of a given Insurance Policy

+ Request (application/x-www-form-urlencoded)

    + Parameters
        + idepol ( required , long , 123456) ...  idepol 
        + numcert ( required , long , 123456) ... numcert
        + numoper ( required , long , 123456) ... numoper

    + Body
    
        ```
        [
        "idepol" : 123456,
        "numcert" : 123456,
        "numoper" : 123456
        ]
        ```

+ Response 200 (application/json)

    ```js
    {
        "parcelas" :
        [
            { 
                "idepol": 123456,
                "numcert": 123456,
                "numoper": 123456,
                "tipo" : "tipo parcela",
                "num": 123456,
                "titulo": "titulo",
                "valor": 12345.95,
                "vencto": "21-10-2013",
                "status": "status" 
            } 
        ],
        "success": "true",
        "formaCobranca": "forma de cobrança",
        "errorMessage" : "Nenhuma parcela encontrada."
    }
    ```

## List Available Dates [/rest/apolice/datasDisponiveis]

List Available Dates of a given Overdue Installment    

### POST

List Available Dates of a given Overdue Installment   

+ Request (application/x-www-form-urlencoded)

    + Parameters
        + idepol ( required , long , 123456) ...  idepol 
        + numcert ( required , long , 123456) ... numcert
        + numoper ( required , long , 123456) ... numoper
        + numeroTitulo ( required , integer , 123456) ... numeroTitulo

    + Body
    
        ```
        [
        "idepol" : 123456,
        "numcert" : 123456,
        "numoper" : 123456,
        "numeroTitulo" : 123456
        ]
        ```

+ Response 200 (application/json)

    ```js
    {
        "datasDiponiveis" :
        [
            data_1: dataDisponivel,
            data_2: dataDisponivel,
            data_n: dataDisponivel          
        ],
        "success": "true",
        "errorMessage" : "Nenhuma data encontrada."
    }
    ```

# Group Oficina

The Oficina Resource

## List Posts of Services [/rest/oficina/listar]

List all referenced Posts of Services

### GET

List all the available Posts of Services

+ Response 200 (application/json)

    ```js
    {
        "oficinas": 
        [
            {
                "endCompleto": "logradouro, numero - bairro - municipio - UF",
                "cep": "000000-00",
                "id": "12345",
                "lat": "-23.611985",
                "lon": "-46.694279",
                "nome": "nome",
                "site": "www.google.com",
                "telDDD": "(11)999999999",
            }
        ],
        "success": true,
        "errorMessage": "Nenhuma oficina encontrada"
    }
    ```


# Group Servico
The Servico Resource

## List Services [/rest/servico]

List Services from a given Insurance Policies

### POST

List all the services available from a given Insurance Policy

+ Request (application/x-www-form-urlencoded)

    + Parameters
        + idepol (Long) ...  idepol 
        + numcert (Long) ... numcert
        + numoper (Long) ... numoper

    + Body
    
        ```
        [
        "idepol" : 123456,
        "numcert" : 123456,
        "numoper" : 123456
        ]
        ```

+ Response 200 (application/json)

    ```js
    {
        "adquirido": 
        [
            {
                "condigo": 123,
                "nome": "nome adquirido",
                "desc": "descricao adquirido"
            }
        ],
        "disponivel":
        [
            {
                "condigo": 456,
                "nome": "nome disponivel",
                "desc": "descricao disponivel"
            }
        ],
        "success": "true"
    }
    ```

# Group Documento

The Documento Resource

## List Documents of a Insurance Policy [/rest/documento/porApolice/{tipo}]

List Documents from a given Insurance Policy .

+ Parameters
    + tipo ( required, string , `auto`) ... Today, there are only two types of Insurance Policy. 'auto' and 'residencia'

### GET

Get list of Documents from Insurance Policies of a given Policy type.

+ Request (application/x-www-form-urlencoded)

    + Parameters
        + idepol (Long) ...  idepol 
        + numcert (Long) ... numcert
        + numoper (Long) ... numoper
        + cdApolice (string) ... cdApolice
        + dsProduto (string) ... dsProduto

    + Body
    
        ```
        [
        "idepol" : 123456,
        "numcert" : 123456,
        "numoper" : 123456,
        "cdApolice" : "A123123",
        "dsProduto" : "A123123"
        ]
        ```

+ Response 200 (application/json)

    ```js
    {
        "documentos":
            [
                {
                    "endosso": 123123,
                    "tipo": : "auto",
                    "cdApolice": "123123",
                    "dsProduto": "123123",
                    "modelo": "modelo",
                    "urlApolice": "url Apolice",
                    "urlCondicoesGerais": "url Condições Gerais",
                    "urlGuiaServicos": "url Guia Serviços"
                }
            ]
        },
        "success": "true",
        "errorMessage" : "Nenhum documento encontrado."
    }
    ```

## List Documents of a User [/rest/documento/porCpf]

List Documents from Insurance Policies of a given user.

### POST

List Documents from Insurance Policies of a given user.

+ Request (application/x-www-form-urlencoded)

    + Parameters
        + cpfcnpj (string) ... CPF or CNPJ
        + placa (string) ... placa
        + chassis (string) ... chassis
        + gerarUrlApolice (boolean) ... apolice
        + urlPublica (boolean) ... url 
        + cdApolice (string) ... cdApolice
        + dsProduto (string) ... dsProduto

    + Body
    
        ```
        [
        "cpfcnpj" : "123.123.123-45",
        ]
        ```

+ Response 200 (application/json)

    ```js
    {
        "documentos":
            [
                {
                    "endosso": 123456,
                    "tipo": : "auto",
                    "cdApolice": "123123",
                    "dsProduto": "123123",
                    "modelo": "modelo",
                    "urlApolice": "url Apolice",
                    "urlCondicoesGerais": "url Condições Gerais",
                    "urlGuiaServicos": "url Guia Serviços"
                }
            ]
        },
        "success": true,
        "errorMessage" : "Nenhum documento encontrado."
    }
    ```

## Send Email [/rest/documento/enviaEmail]

Send email with document URLs

### POST

Send email with document URLs

+ Request (application/x-www-form-urlencoded)

    + Parameters
        + email (string) ... Email Recipient 
        + titulo (string) ... Email title
        + url (string) ... documento url

    + Body
    
        ```
        [
        "email" : "mail@mail.com",
        "titulo" : "titulo",
        "url" : "document url"
        ]
        ```

+ Response 200 (application/json)

    ```js
    {
        "documentos":
            [
                {
                    "endosso": 123123,
                    "tipo": : "auto",
                    "cdApolice": null,
                    "dsProduto": null,
                    "modelo": "modelo",
                    "urlApolice": "url Apolice",
                    "urlCondicoesGerais": "url Condições Gerais",
                    "urlGuiaServicos": "url Guia Serviços"
                }
            ]
        },
        "success": true,
        "errorMessage" : "Nenhum documento encontrado."
    }
    ```

# Group Corretor

The Corretor Resource

## Get Insurance Broker [/rest/corretor]

Get Insurance Broker`s details of a given Insurance Apolicy

### POST

Get Insurance Broker`s details of a given Insurance Apolicy

+ Request (application/x-www-form-urlencoded)

    + Parameters

        + idepol ( required , long , 123456) ...  idepol 
        + numcert ( required , long , 123456) ... numcert
        + numoper ( required , long , 123456) ... numoper

    + Body
        ```
        [
        "idepol" : 123456,
        "numcert" : 123456,
        "numoper" : 123456
        ]
        ```

+ Response 200 (application/json)

    ```js
    {
        "success": true,
        "codigo": 123456,
        "nome": "name",
        "cpfCnpj": "123.123.123-45",
        "logradouro": "logradouro",
        "complemento": "complemento",
        "numero": 123,
        "bairro": "bairro",
        "cidade": "cidade",
        "estado": "estado",
        "cep": "123456-12",
        "errorMessage" : "Ocorreu um erro durante o processamento."
    }
    ```

## List Insurance Brokers [/rest/corretor/listarCorretoresPerimetro/{latitude}/{longitude}]

List Insurance Brokers of a given lat/lon location

+ Parameters
    + latitude ( required, string , `-23.611985`) ... latitude
    + longitude ( required, string , `-46.694279`) ... longitude

### GET

List Insurance Brokers of a given lat/long location 

+ Response 200 (application/json)

    ```js
    {
        "corretores": 
        [ 
            {
                "codigo": 123,
                "nome": "nome",
                "cpfCnpj": "123.123.123-45",
                "logradouro": "logradouro",
                "complemento": "complemento",
                "numero": 123,
                "bairro": "bairro",
                "cidade": "cidade",
                "estado": "estado",
                "cep": "123123-12",
                "telefones": [ 
                                "celular": "(11)12345-1234",
                                "escritorio": "(11)12345-1234"
                            ],
                "email": "email@email.com",
                "latitude": "-23.611985",
                "longitude": "-46.694279"
            }
        ],
        "success": true,
        "errorMessage" : "Nenhum corretor encontrado."
    }
    ```

## Get Insurance Broker of a CEP or Car Plate [/rest/corretor/consultaCorretorApolicePorPlacaOuCep]

Get Insurance Broker`s details of a given CEP number or Car Plate

### POST

Get Insurance Broker`s details of a given CEP number or Car Plate

+ Request (application/x-www-form-urlencoded)

    + Parameters
        + placa ( optional , string , `ABC-1234`) ...  car`s plaque 
        + cep ( optional , string , `12345612`) ... cep number
        
    + Body
    
        ```
        [
        "placa" : "ABC-1234",
        "cep" : "12345612"
        ]
        ```

+ Response 200 (application/json)

    ```js
    {
        "success": "true",
        "corretor": {
            {
                "codigo": 123,
                "nome": "nome",
                "cpfCnpj": "123.123.123-45",
                "logradouro": "logradouro",
                "complemento": "complemento",
                "numero": 123,
                "bairro": "bairro",
                "cidade": "cidade",
                "estado": "estado",
                "cep": "123123-12",
                "telefones": [ 
                                "celular": "(11)12345-1234",
                                "escritorio": "(11)12345-1234"
                            ],
                "email": "email@email.com",
                "latitude": "-23.611985",
                "longitude": "-46.694279"
            }
        },
        "errorMessage" : "Nenhum corretor encontrado."
    }
    ```  
