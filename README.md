# Resolução do desafio

1) Ao abrir a aplicação, foi lido a hint 1. Após isso, foi verificado o nome dos membros da Cartesi no Discord (Cartesians). Com essa dica, pesquisamos mais sobre e vimos que René Descartes iniciou o movimento do cartesianismo. Sua data de nascimento é 1596.
2) Começamos a decodificar a váriavel code que está no dapp.py e foi possível encontrar o número 1593. Portanto, o número de Guess é 3, já que 1596 - 3 = 1593.
3) Por fim, enviamos isso pelo cartesi send e recebemos a resposta mostrada no vídeo.

```
cartesi send generic \
    --dapp=0xab7528bb862fb57e8a2bcd567a2e929a0be56a5e \
    --chain-id=31337 \
    --rpc-url=http://127.0.0.1:8545 \
    --mnemonic-passphrase='test test test test test test test test test test test junk' \
    --input='{"guess": 3, "birth_year_minus_the_guess": 1593}'
```

Vídeo de explicação:
https://github.com/YanMCoutinho/cartesi-code-challenge-2/blob/main/mWYpBO5DjwHUyMoq.mp4

## Código para realizar o decode em python

```
import dis
import marshal
bytecode = (
    b'\xe3\x02\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x04\x00\x00'
    b'\x00\x02\x00\x00\x00C\x00\x00\x00sR\x00\x00\x00d\x01}\x02d\x02}\x03'
    b'|\x02|\x03k\x03r\x19|\x02|\x03k\x04r\x11|\x02|\x038\x00}\x02n\x04'
    b'|\x03|\x028\x00}\x03|\x02|\x03k\x03s\x08|\x02|\x00k\x02r#|\x01d\x03'
    b'k\x02r#d\x04S\x00t\x00d\x05\x83\x01\x01\x00d\x06S\x00)\x07N\xe9\xff'
    b'\xff\x00\x00i\xe9\x01\x00\x00\xe99\x06\x00\x00T\xfa?Error calculating'
    b' GCD of a = 65535 and b = (2**16 >> 7) - 0x17.F)\x01\xda\x05print)'
    b'\x04\xda\x05guess\xda\x1abirth_year_minus_the_guess\xda\x01a\xda\x01b'
    b'\xa9\x00r\t\x00\x00\x00\xfa\x1f<ipython-input-27-d329bfeabe88>\xda\x05'
    b'claim\x05\x00\x00\x00s\x16\x00\x00\x00\x04\x01\x04\x01\x08\x03\x08'
    b'\x01\n\x01\x08\x02\x08\xfc\x10\x06\x04\x01\x08\x02\x04\x01'
)
code_object = marshal.loads(bytecode)
dis.dis(code_object)</code>
```

![success](https://github.com/YanMCoutinho/cartesi-code-challenge-2/assets/69089226/264bce2c-8f8b-49a7-9a94-97126850102e)

<br>
<br>

# O Challenge

<br>

# Challenge: Cartesi Rollups Code Challenge

## Descrição

Este desafio de código é parte da masterclass do @cartesiproject no Brasil, realizada no Inteli. Os participantes devem documentar todo o processo em um README e compartilhar um vídeo no Twitter|X.

## Instruções do Desafio

1.  **Encontrar os Valores Corretos**:
    
    -   Utilize o código fornecido para identificar o valor correto que deve ser adivinhado (guess), bem como outro valor que advém de uma "charada" (birth_year_minus_the_guess). Assim que você conseguir gerar o output correto, mostre-o no explorer que roda na rota: http://localhost:8080/explorer/, faça o "decode" da payload (hex) e mostre a string gerada. Corra! Você precisa ser o primeiro a postar no Twitter|X juntamente com um README.md e um vídeo refazendo os inputs até o decode da string para ganhar o prêmio.

2.  **Documentar o Processo**:
    
    -   Crie um README documentando cada passo que você tomou para encontrar o guess correto. Inclua como você utilizou as funções notice, report e inspect durante o processo. Se possível, use referências para a documentação da Cartesi: https://docs.cartesi.io/.

3.  **Postagem no Twitter|X**:
    
    -   Faça uma postagem no Twitter|X com um vídeo demonstrando a resolução do desafio e o link para o README.md com a explicação. Use o template de mensagem fornecido abaixo e sinta-se à vontade para comentar sobre a experiência da masterclass.


## Template de Mensagem
```text
Estou participando da masterclass da @cartesiproject no Brasil, que está acontecendo no Inteli. 
Aqui está um vídeo demonstrando a resolução do code challenge apresentado hoje. Acesse o link [hyperlink], para ver o README onde explico como resolvi esse desafio. #RollupWithCartesi #CartesiMasterclass
```

## Dicas

-   Você pode utilizar o nonodo para testar mais rapidamente. Nesse caso, o endereço a ser utilizado no `cartesi send` é: 0x70ac08179605AF2D9e75782b8DEcDD3c22aA4D0C
-   Em modo de produção, você pode utilizar o endereço padrão: 0xab7528bb862fb57e8a2bcd567a2e929a0be56a5e

## Passo a Passo

### 1. Configuração do Ambiente

1.  Clone o repositório:
    
```bash
git clone https://github.com/henriquemarlon/cartesi-code-challenge-2.git
```

### 2. Rodando o Código

```bash
cd challenge
cartesi build
cartesi run
```

### 3. Interaja com o dApp:

```bash
cartesi send generic \
    --dapp=<endereço-do-dapp> \
    --chain-id=31337 \
    --rpc-url=http://127.0.0.1:8545 \
    --mnemonic-passphrase='test test test test test test test test test test test junk' \
    --input='{"guess": <valor-aqui>, "birth_year_minus_the_guess": <valor-aqui>}'
```

Envie quantas inputs achar necessário para encontrar os valores certos!

### 4. Encontrando o Guess

Leia o código!
Hint 3: O output esperado é um notice! ;)

### 5. Postagem no Twitter

Grave um vídeo demonstrando o processo e poste no Twitter|X utilizando o template fornecido, junto a um link para um README.md com a explicação da resolução.

## Observações Finais

Boa sorte, Cartesians!
