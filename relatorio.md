# Relatório — Atividade Prática: Sockets TCP

**Disciplina:** Sistemas Distribuídos
**Dupla:** Maria Julia de Melo Honorato
**Data:** 21/11/2026

---

## Nível 1 — Inspecionar o código

### 1.1 Servidor (`servidor.py`)

Descreva com suas palavras o que cada chamada abaixo faz e por que ela
é necessária:

| Chamada | O que ela faz? |
|---------|---------------|
| `socket.socket(AF_INET, SOCK_STREAM)` | cria o socket do servidor com ipv4 e tcp|
| `servidor_socket.bind((HOST, PORTA))` | liga o socket ao ip e a porta|
| `servidor_socket.listen(5)` | faz o servidor comecar a escutar os pedidos dos clientes|
| `servidor_socket.accept()` | pausaate o cliente pedir conexao, e qndo aceita cria um novo socket |
| `conn.recv(TAMANHO_BUFFER)` | le qtd tamanho_biffer de bytes dos dados enviados pelo cliente |
| `conn.sendall(resposta.encode("utf-8"))` | transforma o texto e, bytes e garante o envio ed todos os bytes |
| `conn.close()` | fecha conexao com cliente atual|

### 1.2 Cliente (`cliente.py`)

| Chamada | O que ela faz? |
|---------|---------------|
| `socket.socket(AF_INET, SOCK_STREAM)` | cria socket no msm padrao do servisor |
| `cliente_socket.connect((HOST_SERVIDOR, PORTA_SERVIDOR))` | inicia conxao tcp com host na porta do servidor |
| `cliente_socket.sendall(mensagem.encode("utf-8"))` | converte msg para bytes e envia tudo para o servidor |
| `cliente_socket.recv(TAMANHO_BUFFER)` | pausa ate servidor responder e le ate qntdade de bytes tamanho_buffer|

### 1.3 Rede e contêineres

Por que o cliente usa o hostname `"servidor"` em vez de `"localhost"`
para se conectar? O que aconteceria se usasse `"localhost"`?

> _Resposta:_ porque no docker cada conteiner funciona de forma isolada, entao o nome servidor vai ser ligado ao ip de onde esse servidor esta rodando. se usasse localhost, o cliente iria tentar se conectar dentro dele mesmo, onde nao vai ter ngm escutadno e conexao vaiser recusada

---

## Nível 2 — Modificar o servidor

Descreva as mudanças que você fez no `servidor.py` para:

1. Devolver a mensagem **em maiúsculas**:

   > _O que foi alterado e por quê:_ foi mudado onde a respota é montanda, só usando a função upper() pro texto ser convertiod em letras maiusculas antes de ser enviado de volta

2. Exibir no log o **contador de mensagens recebidas** acumulado:

   > _O que foi alterado e por quê:_ add um incremento da variavel de msg global que ja existia cada vez que uma mensagem chega; e colocado {total_mensagens} dentro do print que ja existia para mostrar a contagem

Após a modificação, você precisou rodar `docker compose up --build`.
Por que o `--build` é necessário aqui?

> _Resposta:_ pro docker nao simplesmente usar a versao antiga que ja estava no computador antes da mudanca no codigo

---

## Observações livres

Anote aqui qualquer comportamento inesperado que observaram, erros que
apareceram e como resolveram, ou dúvidas que ainda têm:

> nao tive muitos problemas, a maioria era relacioanda a como preparar o ambiente usando wsl 

---

## Dúvida para a próxima aula

Escreva **uma pergunta** que surgiu durante a atividade e que vocês
gostariam de ver respondida na aula seguinte: 

> fiz isso para estudar pra prova, entao nao tem mais aula e nao faz mto sentido responder essa
