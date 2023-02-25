## [Tópico T16b] - Álgebra Relacional - Exercícios
###### *by Prof. Plinio Sa Leitao-Junior (INF/UFG)*

Para apoiar os exercícios e exemplo sobre as operações da Álgebra Relacional, considere a ilustração abaixo do **BD Empresa**.

<img src="../media/fig-mr-2.jpg" width="450">

Escreva em álgebra relacional as seguintes consultas:

1. Qual o nome dos projetos que o funcionário "João B Silva" trabalha em?<br>

JOAO_CPF ← π <sub>Cpf</sub> ( σ <sub>Pnome='Joao' AND Minicial='B' AND Unome='Silva'</sub> (FUNCIONARIO) )<br>
JOAO_PNR ← π <sub>Pnr</sub> ( JOAO_CPF ⨝ <sub>Cpf = Fcpf</sub> TRABALHA_EM )<br>
<< expressão para nome dos projetos ?? >><br>

**JOAO_CPF**
|Cpf|
|-|
|12345678966|

**JOAO_PNR**
|Pnr|
|-|
|1|
|2|

JOAO_CPF ← π <sub>Cpf</sub> ( σ <sub>Pnome='Joao' AND Minicial='B' AND Unome='Silva'</sub> (FUNCIONARIO) )<br>
JOAO_PNR ← π <sub>Pnr</sub> ( JOAO_CPF ⨝ <sub>Cpf = Fcpf</sub> TRABALHA_EM )<br>
RESULT ← π <sub>Projnome</sub> ( JOAO_PNR ⨝ <sub>Pnr = Projnumero</sub> PROJETO )<br>

2. Qual o nome das pessoas que trabalham em pelo menos um dos projetos que o funcionário "João B Silva" trabalha em?<br>
_Na sintaxe da ferramenta RelaX ..._<br>
JOAO_CPF = π Cpf ( σ Pnome='Joao' AND Minicial='B' AND Unome='Silva' (FUNCIONARIO) )<br>
JOAO_PNR = π Pnr ( JOAO_CPF ⨝ Cpf = Fcpf TRABALHA_EM )<br>
CPF_RESULT = π Cpf←Fcpf ( JOAO_PNR ⨝ TRABALHA_EM ) - JOAO_CPF<br>
π Pnome, Minicial, Unome (CPF_RESULT ⨝ FUNCIONARIO)<br>

3. Qual o nome das pessoas que não trabalham em qualquer dos projetos que o funcionário "João B Silva" trabalha em? Pessoas que não trabalham em qualquer projeto ESTÃO INCLUÍDAS no resultado da consulta.<br>

4. Qual o nome das pessoas em que todos os projetos que trabalham em estão entre os projetos que o funcionário "João B Silva" trabalha em? Pessoas que não trabalham em qualquer projeto NÃO ESTÃO INCLUÍDAS no resultado da consulta.<br>

IMPORTANTE: Use a sintaxe da Álgebra Relacional conforme os exemplos apresentados até então.
