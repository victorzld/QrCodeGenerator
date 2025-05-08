![Java](https://img.shields.io/badge/java-%23ED8B00.svg?style=for-the-badge&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/springboot-%236DB33F.svg?style=for-the-badge&logo=springboot&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-%23FF9900.svg?style=for-the-badge&logo=amazon-aws&logoColor=white)
![Apache Maven](https://img.shields.io/badge/Apache%20Maven-C71A36?style=for-the-badge&logo=Apache%20Maven&logoColor=white)
![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)

# 📝 QR Code Generator

Uma aplicação Spring Boot que gera QR Code's e os armazena no AWS S3. Esse projeto demonstra a integração da biblioteca ZXing do Google para geração de código QR e do AWS S3 para armazenamento.

## 🚀 Primeiros passos

### Instruções para configurar e executar a aplicação na sua máquina local:

- <a href="https://www.oracle.com/br/java/technologies/downloads/#java21">Java 21 JDK</a>
- <p>Maven</p>
- <a href="https://www.docker.com">Docker</a>
- <p>CLI do AWS configurada com as credenciais apropriadas</p>

### Environment Variables

Crie um arquivo .env na raiz do projeto com as seguintes variáveis:

```bash
AWS_ACCESS_KEY_ID=your_access_key
AWS_SECRET_ACCESS_KEY=your_secret_key
AWS_REGION=your_region
AWS_BUCKET_NAME=your_bucket_name
```

### Desenvolvimento local

1. Crie o arquivo .env conforme descrito acima

2. Build o projeto:

```bash
mvn clean package
```

### Implementação do Docker

1. Build a imagem do Docker:

```bash
docker build -t qrcode-generator:X.X .
```

> Lembre-se de substituir a versão e o nome da imagem, se desejar

2. Execute o contêiner:

```bash
docker run --env-file .env -p 8080:8080 qrcode-generator:X.X
```

> Lembre-se de substituir o caminho do arquivo .env pelo caminho do arquivo de ambiente que você criou.

## Configuração do AWS S3

1. Crie um bucket S3 em sua conta do AWS
2. Atualize o `AWS_BUCKET_NAME` em seu arquivo `.env` ou no comando de execução do Docker
3. Certifique-se de que suas credenciais do AWS tenham as permissões adequadas para acessar o bucket do S3

## 🧱 Diagrama da Arquitetura

<imagem depois

## 🧑‍💻 Tecnologias Utilizadas

- Java 21
- Spring Boot
- Spring Web
- AWS SDK
- Google Zxing
- Docker
- Maven

## API Endpoints

### POST /qrcode

Gere um código QR a partir do texto fornecido e armazene-o no AWS S3. O código QR será gerado como uma imagem PNG com dimensões de 200x200 pixels.

**Parameters**

| Name   | Required | Type   | Description                                                                                                                     |
| ------ | -------- | ------ | ------------------------------------------------------------------------------------------------------------------------------- |
| `text` | required | string | O conteúdo do texto a ser codificado no código QR. Pode ser qualquer valor de string que você queira converter em um código QR. |

**Response**

```json
{
  "url": "https://your-bucket.s3.your-region.amazonaws.com/random-uuid"
}
```

**Error Response**

Se ocorrer um erro durante a geração do código QR ou o upload do S3, a API retornará um erro interno do servidor 500.

**Exemplo de uso**

```bash
curl -X POST http://localhost:8080/qrcode \
     -H "Content-Type: application/json" \
     -d '{"text": "https://example.com"}'
```

## Autor

Feito com 💚 por <a href="https://github.com/victorzld" >victorzld</a>

## License

<a href="/LICENSE" >MIT</a>
