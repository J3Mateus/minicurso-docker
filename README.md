### 🐳 Criação do Docker 

* **Origem:**

  * Criado em **2013** pela empresa **dotCloud, Inc.** (que depois virou **Docker, Inc.**).

* **Motivação:**

  * As **máquinas virtuais** exigiam muito espaço em disco e recursos.
  * Havia problemas de **desempenho e corrupção de aplicações** nas VMs.
  * Surgiu a necessidade de uma solução **mais leve e eficiente**.

* **Tecnologia base:**

  * O **LXC (Linux Containers)**, criado em **2008**, permitia criar **instâncias isoladas** de um sistema operacional dentro de outro.
  * Essa tecnologia foi a **base para o Docker**.

* **Adoção e impacto:**

  * O Docker trouxe **facilidade de uso e portabilidade**.
  * Houve um **grande crescimento no mercado**, pois os desenvolvedores podiam **rodar suas aplicações do notebook direto para a produção**.



### 🐳 O que é Docker  ? 

* **Docker** é uma ferramenta que ajuda a empacotar programas dentro de uma **“caixinha” chamada *container***.
* Dentro dessa caixinha, colocamos **tudo o que o programa precisa** para funcionar — como bibliotecas, dependências e configurações.
* Isso faz com que o programa **funcione do mesmo jeito em qualquer computador**, sem precisar reinstalar ou configurar tudo de novo.
* Com o Docker, você **cria uma vez** e **roda em qualquer lugar** (no seu PC, no servidor ou na nuvem).
* Em resumo:

  > Docker é como colocar seu programa dentro de uma **mala com tudo que ele precisa**. Onde quer que você leve essa mala, o programa vai rodar igual.



---

### 🐳 Por que usar Docker?

* **Facilita o trabalho em equipe:**

  * Desenvolvedores escrevem e compartilham código facilmente por meio de *containers Docker*.

* **Ambiente padronizado:**

  * O mesmo container pode ser usado no **desenvolvimento**, **teste** e **produção**, evitando o famoso “na minha máquina funciona”.

* **Agilidade nos testes:**

  * É simples enviar o aplicativo para um **ambiente de teste** e rodar **testes automatizados ou manuais**.

* **Correções rápidas:**

  * Se algo der errado, o desenvolvedor **corrige no container** e **reimplanta facilmente** para novos testes.

* **Implantação simplificada:**

  * Depois de aprovado, basta **enviar a imagem atualizada** para o **ambiente de produção** — rápido, consistente e sem complicações.




### 🐳 O que é um *Container*?

* **Container** é uma espécie de **ambiente isolado** onde você executa uma aplicação junto com tudo o que ela precisa para funcionar.
* Dentro desse ambiente vai **o código do programa**, **bibliotecas**, **dependências**, **configurações** e até partes do sistema operacional.
* Ele garante que sua aplicação rode **sempre do mesmo jeito**, independentemente do computador, servidor ou sistema onde ela está sendo executada.
* Containers são **leves** porque compartilham o **kernel do sistema operacional** com a máquina host — diferente de máquinas virtuais, que precisam carregar um sistema operacional inteiro.
* Eles também são **rápidos de criar, destruir e mover**, tornando o desenvolvimento e a implantação muito mais ágeis.

---

#### Em resumo:

> **Container é como uma “caixinha isolada” que carrega seu aplicativo com tudo o que ele precisa, garantindo que ele funcione igual em qualquer lugar.**

---

### 🛠️ Parte prática (exemplo)

```bash
docker run docker/whalesay cowsay boo
```



### 🐳 Diferença entre **Imagem** e **Container**

* **Imagem (Image)**

  * É como um **modelo**, um **molde**, uma **receita pronta**.
  * Contém **todo o necessário** para criar um container: código, dependências, configurações e instruções.
  * É **imutável** — uma vez criada, **não muda**.
  * Você pode pensar nela como um **arquivo estático** que descreve como o container deve ser.

---

* **Container**

  * É a **execução real** de uma imagem.
  * Quando você roda uma imagem, você cria um **container**, que é um ambiente isolado e em funcionamento.
  * Ele é **mutável durante a execução** — você pode instalar coisas, alterar arquivos etc.
  * Containers existem apenas enquanto estão rodando (ou até você salvá-los).
  * São como **instâncias vivas** geradas a partir da imagem.

---

### 🎯 Resumo simples:

> **Imagem** = *Receita, o molde, o pacote pronto.*
> **Container** = *O prato sendo servido, a execução viva da receita.*

Ou:

> A **imagem** é o **plano**.
> O **container** é a **execução** desse plano.


### 🐳 Onde encontrar imagens Docker?

* Em **registries** (repositórios de imagens).
* Principal: **Docker Hub** — onde você pode **buscar imagens**, **ver quais existem** e **ler a documentação de uso**.
* Outros: **GitHub CR**, **AWS ECR**, **GCR**, **ACR**.

---

### 🐳 Como rodar uma imagem?

```bash
docker run <nome-da-imagem>
```

* O Docker **baixa** (se precisar) e **executa** a imagem como um container.

---

### 📝 Resumo

> No **Docker Hub** você encontra imagens, vê quais existem e aprende como usar. Para rodar, basta executar `docker run`.




### 🐳 Como visualizar containers no Docker

#### 🔵 Containers em execução (rodando)

```bash
docker ps
```

Mostra somente os containers **ativos**.

---

#### ⚪ Containers parados

```bash
docker ps -f status=exited
```

Exibe apenas os containers **finalizados**.

---

#### 🟢 Todos os containers (rodando + parados)

```bash
docker ps -a
```

Lista **todos** os containers existentes no sistema.

---

### ❓ Por que usamos esses comandos?

* Para **monitorar** quais containers estão rodando.
* Para **identificar problemas** (containers parando, falhando, reiniciando).
* Para **organizar o ambiente**, limpando containers que não são mais usados.
* Para **verificar o status** antes de iniciar, parar ou remover containers.
* Para **auditar** o que está ocupando recursos na máquina (CPU, memória, portas).

---

### 🏷️ Flags mais comuns do `docker ps`

* **`-a`** → mostra **todos** os containers
* **`-q`** → exibe somente os **IDs**
* **`-f`** → permite **filtrar** por status, nome, ID etc.
* **`--format`** → personaliza a forma como os dados são exibidos

---

### 📝 Resumo

> Usamos `docker ps` para **ver o estado dos containers**, entender o que está rodando e manter o ambiente organizado. `docker ps -a` mostra tudo, e filtros como `-f` ajudam a encontrar exatamente o que você precisa.






### 🐳 O que é o comando `docker run`?

* O `docker run` é usado para **criar e iniciar um container** a partir de uma imagem.
* Ele baixa a imagem (se não existir), cria o container e executa o processo definido nela.
* É um dos **comandos mais importantes do Docker**, pois é com ele que realmente “colocamos o container para funcionar”.

---

### 🏷️ Flags mais comuns do `docker run`

#### 🔹 **`-d`** — Executar em segundo plano (*detached*)

```bash
docker run -d nginx
```

O container roda em **background**, sem travar o terminal.

---

#### 🔹 **`-p`** — Mapear portas

```bash
docker run -p 8080:80 nginx
```

Expõe a porta do container para a máquina host.

---

#### 🔹 **`--name`** — Dar um nome ao container

```bash
docker run --name meu-nginx nginx
```

Facilita para parar, iniciar e remover depois.

---

#### 🔹 **`-e`** — Variáveis de ambiente

```bash
docker run -e MYSQL_ROOT_PASSWORD=123 mysql
```

Define variáveis usadas pela aplicação dentro do container.

---

#### 🔹 **`-v`** — Criar volumes (persistência de dados)

```bash
docker run -v meuVolume:/data nginx
```

Permite salvar dados mesmo após o container ser apagado.

---

#### 🔹 **`--rm`** — Remover o container ao finalizar

```bash
docker run --rm ubuntu echo "Oi"
```

Bom para testes rápidos.

---

#### 🔹 **`-it`** — Modo interativo + terminal

```bash
docker run -it ubuntu bash
```

Abre um terminal **dentro do container**.

---

### 📝 Resumo

> O `docker run` serve para **criar e executar containers**.
> Suas flags permitem controlar **porta, nome, volumes, ambiente, execução em background** e muito mais.


### 🐳 Comandos essenciais para gerenciar containers

---

### 🔴 **Parar um container — `docker stop`**

```bash
docker stop <nome-ou-id>
```

* Envia um sinal para **encerrar o container de forma segura**.
* Usado quando você quer finalizar um serviço sem apagá-lo.

---

### 🟢 **Reiniciar um container — `docker restart`**

```bash
docker restart <nome-ou-id>
```

* Para e inicia o container novamente.
* Útil após **alterações de configuração** ou para resolver falhas temporárias.

---

### 🗑️ **Remover um container — `docker rm`**

```bash
docker rm <nome-ou-id>
```

* **Apaga** um container que já está parado.
* Libera espaço e mantém o ambiente organizado.
* Para remover todos os containers de uma vez:

```bash
docker rm $(docker ps -aq)
```

---

### 📄 **Ver logs do container — `docker logs`**

```bash
docker logs <nome-ou-id>
```

* Mostra o **histórico de saída** da aplicação dentro do container.
* Usado para **debug**, erros, mensagens do servidor etc.

#### Flags úteis do `docker logs`:

* **`-f`** → segue os logs em tempo real

  ```bash
  docker logs -f meu-container
  ```

* **`--tail <n>`** → mostra apenas as últimas *n* linhas

  ```bash
  docker logs --tail 50 meu-container
  ```

---

### 📝 Resumo

> **stop** = parar
> **restart** = reiniciar
> **rm** = remover
> **logs** = visualizar mensagens e erros do container

Esses comandos ajudam a **controlar, depurar e organizar** seus containers no dia a dia.





