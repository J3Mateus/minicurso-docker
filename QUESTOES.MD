## **1. Rodar um container simples**

Execute um container usando a imagem `hello-world`.
Qual comando você deve usar?

---

## **2. Listar containers rodando**

Depois de rodar o `hello-world`, liste todos os containers ativos.
Qual comando faz isso?

---

## **3. Baixar e rodar uma imagem na porta certa**

Baixe (pull) a imagem `nginx` e rode um container que fique acessível na porta 8080 do seu computador.
Comandos esperados: 1 para baixar, 1 para rodar.

---

## **4. Parar um container**

Pare o container do Nginx que você subiu.
Qual comando você usa?

---

## **5. Remover um container parado**

Depois de parar, remova o container Nginx.
Qual comando faz isso?

---

## **6. Criar um arquivo e disponibilizar no container (bind mount)**

Crie um arquivo no host chamado `index.html` com o texto “Olá Docker”.
Depois execute um Nginx montando esse arquivo em:
`/usr/share/nginx/html/index.html`.
Qual comando você usar para montar esse arquivo?

---

## **7. Ver logs de um container**

Rode um container `nginx` novamente e depois veja seus logs.
Qual comando mostra os logs?

---

## **8. Executar um comando dentro do container**

Rode o container Nginx e depois abra um shell dentro dele (bash ou sh).
Qual comando permite “entrar” no container?

---

## **9. Criar uma imagem simples**

Crie um arquivo `Dockerfile` contendo:

```
FROM alpine
CMD echo "Minha primeira imagem"
```

Depois construa a imagem com o nome `minhaimg`.
Qual comando constrói a imagem?

---

## **10. Criar um docker-compose simples**

Crie um arquivo `docker-compose.yml` com apenas 1 serviço chamado `web`, usando a imagem `nginx`, exposta na porta 8080.
Depois execute esse serviço com Docker Compose.
Qual comando você usa para subir o compose?
