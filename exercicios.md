# Lista de Exercícios Práticos — Redis CLI

> Execute os comandos no `redis-cli` e adicione os prints dos resultados abaixo de cada exercício.

---

# Exercício 1 — Cadastro de Usuário

## Comandos

```bash
SET usuario "Carlos"
GET usuario

SET usuario "Carlos Silva"
GET usuario
```

## Prints

![exercicio 01](image-1.png)

---

# Exercício 2 — Cadastro de Produto

## Comandos

```bash
MSET produto "Notebook" preco "3500" estoque "15"

MGET produto preco estoque
```

## Prints

![exercicio 02](image-2.png)

---

# Exercício 3 — Controle de Login

## Comandos

```bash
SETNX admin "true"

SETNX admin "false"

GET admin
```

## Prints

![exercicio 03](image-3.png)

---

# Exercício 4 — Nome Completo

## Comandos

```bash
SET nome "Maria"

APPEND nome " Oliveira"

STRLEN nome

GETRANGE nome 0 4
```

## Prints

![exercicio 04](image-4.png)

---

# Exercício 5 — Alteração Parcial

## Comandos

```bash
SET cidade "Campinas"

SETRANGE cidade 0 "São "

GET cidade
```

## Prints

![exercicio 05](image-5.png)

> Observação:
> O comando `SETRANGE` opera em bytes. Como o caractere `ã`
> utiliza múltiplos bytes em UTF-8, o resultado pode aparecer
> como `"S\xc3\xa3o nas"` dependendo do terminal utilizado.

---

# Exercício 6 — Sistema de Pontuação

## Comandos

```bash
SET pontos 10

INCR pontos

INCRBY pontos 5

DECRBY pontos 3

GET pontos
```

## Prints

![exercicio 06](image-6.png)

---

# Exercício 7 — Carteira Digital

## Comandos

```bash
SET saldo 100.50

INCRBYFLOAT saldo 25.75

GET saldo
```

## Prints

![exercicio 07](image-7.png)

---

# Exercício 8 — Token Temporário

## Comandos

```bash
SET token "abc123" EX 60

TTL token

PERSIST token

TTL token
```

## Prints

![exercicio 08](image-8.png)

---

# Exercício 9 — Expiração em Milissegundos

## Comandos

```bash
SET sessao "ativa"

PEXPIRE sessao 5000

PTTL sessao
```

## Prints

![exercicio 09](image-9.png)

---

# Exercício 10 — Gerenciamento de Chaves

## Comandos

```bash
SET curso "Redis"

RENAME curso disciplina

COPY disciplina backup_disciplina

TYPE disciplina

EXISTS disciplina

DEL disciplina
```

## Prints

![exercicio 10](image-10.png)

---

# Exercício 11 — Banco Redis

## Comandos

```bash
SET chave_teste "valor"

MOVE chave_teste 1

SELECT 1

GET chave_teste
```

## Prints

![exercicio 11](image-11.png)

---

# Exercício 12 — Listagem de Chaves

## Comandos

```bash
SET chave1 "A"
SET chave2 "B"
SET chave3 "C"
SET chave4 "D"
SET chave5 "E"

KEYS *

SCAN 0
```

## Prints

![exercicio 12](image-12.png)

---

# Exercício 13 — Lista de Tarefas

## Comandos

```bash
RPUSH tarefas "Estudar Redis"
RPUSH tarefas "Fazer Exercícios"
RPUSH tarefas "Dormir"

LRANGE tarefas 0 -1
```

## Prints

![exercicio 13](image-13.png)

---

# Exercício 14 — Controle de Fila

## Comandos

```bash
LLEN tarefas

LINDEX tarefas 0

LINDEX tarefas -1
```

## Prints

![exercicio 14](image-14.png)

---

# Exercício 15 — Alteração de Item

## Comandos

```bash
LSET tarefas 1 "Fazer Projeto"

LRANGE tarefas 0 -1
```

## Prints

![exercicio 15](image-15.png)

---

# Exercício 16 — Inserção Estratégica

## Comandos

```bash
LINSERT tarefas BEFORE "Dormir" "Tomar Café"

LRANGE tarefas 0 -1
```

## Prints

![exercicio 16](image-16.png)

---

# Exercício 17 — Remoção de Elementos

## Comandos

```bash
LPOP tarefas

RPOP tarefas

LRANGE tarefas 0 -1
```

## Prints

![exercicio 17](image-17.png)
---

# Exercício 18 — Movendo Itens Entre Filas

## Comandos

```bash
RPUSH fila_atividade_pendente "Atividade 1"
RPUSH fila_atividade_pendente "Atividade 2"

LMOVE fila_atividade_pendente fila_atividade_processando LEFT RIGHT

LRANGE fila_atividade_pendente 0 -1

LRANGE fila_atividade_processando 0 -1
```

## Prints

![exercicio 18](image-18.png)

---

# Exercício 19 — Histórico Limitado

## Comandos

```bash
RPUSH logs "cmd1"
RPUSH logs "cmd2"
RPUSH logs "cmd3"
RPUSH logs "cmd4"
RPUSH logs "cmd5"
RPUSH logs "cmd6"
RPUSH logs "cmd7"
RPUSH logs "cmd8"
RPUSH logs "cmd9"
RPUSH logs "cmd10"

LTRIM logs -5 -1

LRANGE logs 0 -1
```

## Prints

![exercicio 19](image-19.png)

---

# Exercício 20 — Remoção por Valor

## Comandos

```bash
RPUSH tarefas "Dormir"
RPUSH tarefas "Dormir"
RPUSH tarefas "Dormir"

LREM tarefas 1 "Dormir"

LRANGE tarefas 0 -1

LREM tarefas 0 "Dormir"

LRANGE tarefas 0 -1
```

## Prints

![exercicio 20](image-20.png)

---

# Exercício 21 — Localização de Elementos

## Comandos

```bash
LPOS tarefas "Estudar Redis"

LPOS tarefas "Dormir" COUNT 10
```

## Prints

![exercicio 21](image-21.png)

---

# Exercício 22 — Remoção Múltipla

## Comandos

```bash
LPUSH tarefas "Item1" "Item2" "Item3" "Item4"

LTRIM tarefas 0 1

LRANGE tarefas 0 -1
```

## k

![exercicio 22](image-22.png)

---

# Exercício 23 — Expiração em Listas

## Comandos

```bash
RPUSH lista_temporaria "A"
RPUSH lista_temporaria "B"

EXPIRE lista_temporaria 10

TTL lista_temporaria

EXISTS lista_temporaria
```

## Prints

![exercicio 23](image-23.png)

# Desafio 

## Com base nos comandos do Redis apresentados e utilizados nesta lista de exercícios, crie um script exemplificando um mini fluxo de um problema que você identifique no seu cotidiano, podendo ser no seu trabalho, nos seus estudos ou na sociedade.

```bash
# MINI FLUXO REDIS - CONTROLE DE ENCOMENDAS
# Queijaria / Laticínios (@queijosdelatte)

# Problema identificado:
# Organização manual dos pedidos e entregas,
# dificultando o controle de clientes,
# produtos e status das encomendas.

# 1. Cadastro de clientes

HSET cliente:1 nome "Maria Silva" telefone "14999999999" cidade "Marilia"

HSET cliente:2 nome "Joao Souza" telefone "14988888888" cidade "Pompeia"

# Visualizar cliente
HGETALL cliente:1

# 2. Cadastro de produtos

HSET produto:1 nome "Requeijao de Corte 500g" preco "45.00" estoque "20"

HSET produto:2 nome "Doce de Leite 500g" preco "28.00" estoque "15"

# Consultar produto
HGETALL produto:1

# 3. Registro de pedidos

HSET pedido:1001 cliente "Maria Silva" produto "Requeijao de Corte" quantidade "2" status "Em preparo"

HSET pedido:1002 cliente "Joao Souza" produto "Doce de Leite" quantidade "1" status "Aguardando pagamento"

# Consultar pedido
HGETALL pedido:1001

# 4. Lista de pedidos para entrega

LPUSH entregas "Pedido 1001 - Maria Silva"

LPUSH entregas "Pedido 1002 - Joao Souza"

# Visualizar fila de entregas
LRANGE entregas 0 -1

# 5. Atualização do status do pedido

HSET pedido:1001 status "Saiu para entrega"

# Verificar atualização
HGET pedido:1001 status

# 6. Controle de estoque

# Venda de 2 unidades do requeijão
HINCRBY produto:1 estoque -2

# Consultar estoque atualizado
HGET produto:1 estoque

# 7. Histórico de pedidos concluídos

SADD pedidos_concluidos 1001

# Visualizar pedidos concluídos
SMEMBERS pedidos_concluidos

# 8. Relatório rápido

# Quantidade de pedidos na fila
LLEN entregas

# Quantidade de pedidos concluídos
SCARD pedidos_concluidos
```
