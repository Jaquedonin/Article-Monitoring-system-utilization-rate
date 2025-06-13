# Article-Monitoring-system-utilization-rate
### EN ###
## CPU Simulations ##
For CPU processing, the environment was built using a virtual machine - MV, created in Virtual Box and configured with the necessary dependencies. Each scenario has different resources in terms of \textit{hardware}. The following dependencies were used to run the tests:

- Virtual Box version 6.1[^1]
- YOLO architecture version 8.0[^2]
- Pip version 22.0[^3]
- Python version 3.10[^4]
- Ubuntu 22.04 LTS version *server*[^5]
- Github[^6]
- Packages numpy[^7], torch[^8], opencv[^9] and ultralytics[^10]

For both CPU and GPU simulations, a random arrival rate was used to simulate the Poisson distribution. Figure 01 shows this distribution over time.

![Time between arrivals graph](https://github.com/user-attachments/assets/e3ebf7b5-70ad-4960-aa69-6256d400a0f9)

*Figure 01: Time between arrivals graph*

![Teste_1cpu (1)](https://github.com/user-attachments/assets/2b4ff02c-0a2a-4dc2-9a9e-767abe103c65)

*Figure 02: Service time graph*

![Teste_1cpu (2)](https://github.com/user-attachments/assets/d9d38f9a-02f6-4907-836b-94dc2d566c27)

*Figure 03: Graph of the waiting time*

| scenario | $\rho$       |
|---------|--------------|
| MV-1    | $\approx 9,07$ |
| MV-2    | $\approx 9,06$ |
| MV-3    | $\approx 5,25$ |
| MV-4    | $\approx 5,05$ |
| MV-5    | $\approx 4,93$ |
| MV-6    | $\approx 4,39$ |
| MV-7    | $\approx 4,31$ |

*Table 01: System utilization rate values ​​for the M/M/1 model of all VMs.*

The Utilization Rate $\rho$ is given by:

$$
\rho = \frac{\lambda}{c \cdot \mu} = \frac{1000}{1 \times 110.19} \approx 9.07
$$

The Average Waiting Time in Queue $W_q$ is given by:

$$
W_q = \frac{\rho}{\mu (1 - \rho)}
$$

The denominator $1 - \rho$ is negative, resulting in a negative value for \(W_q\), indicating that the formula does not apply to an unstable system.

The Average Time in System $W$ is given by:

$$
W = W_q + \frac{1}{\mu}
$$

Since $W_q$ is negative, the total time in the system is also negative, which does not match reality, so it is necessary to adjust the queue model.

The Average Number of Customers in Queue $L_q$ is given by:

$$
L_q = \lambda \cdot W_q
$$

This also results in a negative value.

The Average Number of Customers in System $L$ is given by:

$$
L = L_q + \frac{\lambda}{\mu}
$$

Since $L_q$ is negative, $L$ is also inconsistent.

| Parameter | Value |
|-----------|-------|
| Number of Servers | 10 |
| Utilization Rate $\rho$ | 0.9074 |
| Average waiting time in queue $W_q$ (minutes) | 0.00678 |
| Average time in system $W$ (minutes) | 0.01585 |
| Average number of customers in queue $L_q$ | 6.78005 |
| Average number of customers in system $L$ | 15.85501 |
| Average number of busy servers | 9.07496 |

*Table 02: Waiting and system utilization parameters for MV-1.*

Table 03 presents the values ​​obtained for the new queue model with $c = 10$.

| MV | $c$ | $W_q$ | $W$ | $L_q$ | $L$ | $c_{ocup}$ | $\rho$ |
|----|-----|-------|-------|-------|-------|------------|--------|
| 1  | 10  | $\approx 0,0075$ | $\approx 0,0165$ | $\approx 7,4712$ | $\approx 16,5461$ | $\approx 7,4712$ | 90,75% |
| 2  | 10  | $\approx 0,0074$ | $\approx 0,0164$ | $\approx 7,3729$ | $\approx 16,4391$ | $\approx 7,3729$ | 90,66% |
| 3  | 6   | $\approx 0,0055$ | $\approx 0,0107$ | $\approx 5,4618$ | $\approx 10,7132$ | $\approx 5,4618$ | 87,52% |
| 4  | 6   | $\approx 0,0038$ | $\approx 0,0089$ | $\approx 3,8383$ | $\approx 8,8903$ | $\approx 3,8383$ | 84,2% |
| 5  | 6   | $\approx 0,0033$ | $\approx 0,0082$ | $\approx 3,2578$ | $\approx 8,2082$ | $\approx 3,2578$ | 82,51% |
| 6  | 5   | $\approx 0,0060$ | $\approx 0,0104$ | $\approx 5,9528$ | $\approx 10,3503$ | $\approx 5,9528$ | 87,95% |
| 7  | 5   | $\approx 0,0050$ | $\approx 0,0093$ | $\approx 5,0265$ | $\approx 9,3462$ | $\approx 5,0265$ | 86,4% |

*Table 03: Table of the number of servers, queue waiting parameters and system utilization in all VMs.*

## GPU simulation ##

The GPU test scenario was built using Docker to create the processing environment, configured with the necessary dependencies. The following dependencies were used to run the tests:

- Ubuntu 22.04 WSL[^11]
- Docker[^12]
- Python version 3.10 or higher[^13]
- Inference Docker image[^14]
- Docker image of the API that receives the images[^15]






### PT-BR ###
## Simulações em CPU ##
Para o processamento em CPU, o ambiente foi construído utilizando máquina virtual - MV, criada no Virtual Box e configurada com as dependências necessárias. Cada cenário possui diferentes recursos em termos de \textit{hardware}. As seguintes dependências foram utilizadas para a execução dos testes:

- Virtual Box versão 6.1[^1]  
- Arquitetura YOLO versão 8.0[^2]  
- Pip versão 22.0[^3]  
- Python versão 3.10[^4]  
- Ubuntu 22.04 LTS versão *server*[^5]  
- Github[^6]  
- Pacotes numpy[^7], torch[^8], opencv[^9] e ultralytics[^10]  

[^1]: [https://www.virtualbox.org/](https://www.virtualbox.org/)  
[^2]: [https://github.com/ultralytics/ultralytics](https://github.com/ultralytics/ultralytics)  
[^3]: [https://pip.pypa.io/en/stable/](https://pip.pypa.io/en/stable/)  
[^4]: [https://www.python.org/downloads/release/python-3100/](https://www.python.org/downloads/release/python-3100/)  
[^5]: [https://releases.ubuntu.com/jammy/](https://releases.ubuntu.com/jammy/)  
[^6]: [https://github.com/](https://github.com/)  
[^7]: [https://pypi.org/project/numpy/](https://pypi.org/project/numpy/)  
[^8]: [https://pypi.org/project/torch/](https://pypi.org/project/torch/)  
[^9]: [https://pypi.org/project/opencv-python/](https://pypi.org/project/opencv-python/)  
[^10]: [https://pypi.org/project/ultralytics/](https://pypi.org/project/ultralytics/)  

Para as simulações, tanto CPU quanto GPU, foi utilizada uma taxa de chegada randômica a fim de simular a distribuição de Poisson. A Figura 01 mostra essa distribuição ao longo do tempo.


![Gráfico de tempo entre as chegadas](https://github.com/user-attachments/assets/e3ebf7b5-70ad-4960-aa69-6256d400a0f9)

*Figura 01: Gráfico de tempo entre as chegadas*


![Teste_1cpu (1)](https://github.com/user-attachments/assets/2b4ff02c-0a2a-4dc2-9a9e-767abe103c65)

*Figura 02: Gráfico de tempo de serviço*

![Teste_1cpu (2)](https://github.com/user-attachments/assets/d9d38f9a-02f6-4907-836b-94dc2d566c27)

*Figura 03: Gráfico do tempo de espera*

| Cenário | $\rho$       |
|---------|--------------|
| MV-1    | $\approx 9,07$ |
| MV-2    | $\approx 9,06$ |
| MV-3    | $\approx 5,25$ |
| MV-4    | $\approx 5,05$ |
| MV-5    | $\approx 4,93$ |
| MV-6    | $\approx 4,39$ |
| MV-7    | $\approx 4,31$ |

*Tabela 01: Valores de taxa de utilização dos sistemas para o modelo M/M/1 de todas as MVs.*

A Taxa de Utilização $\rho$ é dada por:

$$
\rho = \frac{\lambda}{c \cdot \mu} = \frac{1000}{1 \times 110,19} \approx 9,07
$$

O Tempo Médio de Espera na Fila $W_q$ é dado por:

 $$
 W_q = \frac{\rho}{\mu (1 - \rho)}
 $$
   
O denominador $1 - \rho$ é negativo, resultando em um valor negativo para \(W_q\), indicando que a fórmula não se aplica para um sistema instável.

O Tempo Médio no Sistema $W$ é dado por:
   
 $$
 W = W_q + \frac{1}{\mu}
 $$
   
Como $W_q$ é negativo, o tempo total no sistema também é negativo, o que não condiz com a realidade, portanto, é necessário ajustar o modelo de fila.

O Número Médio de Clientes na Fila $L_q$ é dado por:
  
 $$
 L_q = \lambda \cdot W_q
 $$
   
Isso também resulta em um valor negativo.

O Número Médio de Clientes no Sistema $L$ é dado por:
  
 $$
 L = L_q + \frac{\lambda}{\mu}
 $$
   
Como $L_q$ é negativo, $L$ também é inconsistente.

| Parâmetro | Valor |
|-----------|-------|
| Número de servidores | 10 |
| Taxa de Utilização $\rho$ | 0,9074 |
| Tempo médio de espera na fila $W_q$ (minutos) | 0,00678 |
| Tempo médio no sistema $W$ (minutos) | 0,01585 |
| Número médio de clientes na fila $L_q$ | 6,78005 |
| Número médio de clientes no sistema $L$ | 15,85501 |
| Número médio de servidores ocupados | 9,07496 |

*Tabela 02: Parâmetros de espera e utilização do sistema para MV-1.*

A Tabela 03  apresenta os valores obtidos para o novo modelo de fila com $c = 10$.

| MV | $c$ | $W_q$ | $W$ | $L_q$ | $L$ | $c_{ocup}$ | $\rho$ |
|----|-----|-------|-------|-------|-------|------------|--------|
| 1  | 10  | $\approx 0,0075$ | $\approx 0,0165$ | $\approx 7,4712$ | $\approx 16,5461$ | $\approx 7,4712$ | 90,75% |
| 2  | 10  | $\approx 0,0074$ | $\approx 0,0164$ | $\approx 7,3729$ | $\approx 16,4391$ | $\approx 7,3729$ | 90,66% |
| 3  | 6   | $\approx 0,0055$ | $\approx 0,0107$ | $\approx 5,4618$ | $\approx 10,7132$ | $\approx 5,4618$ | 87,52% |
| 4  | 6   | $\approx 0,0038$ | $\approx 0,0089$ | $\approx 3,8383$ | $\approx 8,8903$ | $\approx 3,8383$ | 84,2% |
| 5  | 6   | $\approx 0,0033$ | $\approx 0,0082$ | $\approx 3,2578$ | $\approx 8,2082$ | $\approx 3,2578$ | 82,51% |
| 6  | 5   | $\approx 0,0060$ | $\approx 0,0104$ | $\approx 5,9528$ | $\approx 10,3503$ | $\approx 5,9528$ | 87,95% |
| 7  | 5   | $\approx 0,0050$ | $\approx 0,0093$ | $\approx 5,0265$ | $\approx 9,3462$ | $\approx 5,0265$ | 86,4% |

*Tabela 03: Tabela do número de servidores, parâmetros de espera na fila e utilização do sistema em todas as MVs.*

## Simulação em GPU ##

O cenário de teste em GPU foi construído utilizando o Docker para criação do ambiente de processamento, configurado com as dependências necessárias. As seguintes dependências foram utilizadas para a execução dos testes:

- Ubuntu 22.04 WSL[^11]
- Docker[^12]
- Python versão 3.10 ou superior[^13]
- Imagem docker de inferência[^14]
- Imagem docker da API que recebe as imagens[^15]

[^11]: [https://ubuntu.com/desktop/wsl](https://ubuntu.com/desktop/wsl)
[^12]: [https://www.docker.com/](https://www.docker.com/)
[^13]: [https://www.python.org/downloads/release/python-3120/](https://www.python.org/downloads/release/python-3120/)
[^14]: [https://hub.docker.com/r/pedromalheiros/yolo-inference-image-processing-architecture](https://hub.docker.com/r/pedromalheiros/yolo-inference-image-processing-architecture)
[^15]: [https://hub.docker.com/r/pedromalheiros/yolo-api-image-processing-architecture](https://hub.docker.com/r/pedromalheiros/yolo-api-image-processing-architecture)


![GPU_1](https://github.com/user-attachments/assets/1ff53f50-85fb-4e02-bdfe-a9995f5a0a52)

*Figura 04: Gráfico de tempo de serviço.*

![GPU_2](https://github.com/user-attachments/assets/d98f8241-5216-41bb-87bc-55fa22c09b99)

*Figura 05: Gráfico do tempo de espera.*


A Taxa de Utilização do Sistema $\rho$ é dada por:

   $$
   \rho = \frac{\lambda}{c \cdot \mu}
   $$
   
Substituindo os valores:
   
   $$
   \rho = \frac{1000}{1 \times 3301,86} = 0,303
   $$
   
Isso significa que, em média, 30,3% da capacidade do servidor está sendo utilizada.

O Tempo Médio de Espera na Fila $W_q$ para sistemas M/M/1 é dado por:
  
   $$
   W_q = \frac{0,303}{3301,86 \times (1 - 0,303)}
   $$
   
   $$
   W_q \approx 0,0004
   $$
   
O que indica que um cliente espera cerca de $0,000132$ milissegundos antes de ser atendido.

O Tempo Médio Gasto no Sistema $W$ é dados pelo tempo total que um cliente passa no sistema (espera + atendimento) e é dado por:
   
   $$
   W = 0,000132 + \frac{1}{3301,86}
   $$
   
   $$
   W \approx 0,0007
   $$
   
   Isso significa que, em média, um cliente passa cerca de $0,000435$ milissegundos no sistema.

O Número Esperado de Clientes na Fila $L_q$ é dado por:
   
   $$
   L_q = 1000 \times 0,000132 = 0,4344
   $$
   
Isso significa que, em média, há $0,4344$ clientes esperando na fila.

O Número Esperado de Clientes no Sistema $L$  é:
  
   $$
   L = 1000 \times 0,000435 =  0,7373
   $$
   
Ou seja, o sistema tem, em média, $0,4344$ clientes (fila + atendimento).

Como há apenas um servidor, a ocupação é simplesmente:
   
   $$
   c_{ocupados} = \rho \times c = 0,303 \times 1 = 0,303
   $$
   
Isso significa que, em média, 30,3% do tempo o servidor está ocupado. Diferentemente das simulações em CPU apresentadas anteriormente, neste caso, o modelo M/M/1 atende a demanda do sistema. Na verdade, acontece uma subutilização da GPU, visto que em apenas 30% do tempo, o servidor permanece ocupado.

| **Parâmetro** | **Fórmula** | **Valor Aproximado** | **Descrição** |
|---------------|-------------|----------------------|---------------|
| Tempo Médio de Espera na Fila ($W_q$) | $\frac{0,303}{3301,86 \times (1 - 0,303)}$ | $\approx 0,0004$ | Um cliente espera cerca de 0,000132 milissegundos antes de ser atendido. |
| Tempo Médio Gasto no Sistema ($W$) | $0,000132 + \frac{1}{3301,86}$ | $\approx 0,0007$ | Um cliente passa cerca de 0,000435 milissegundos no sistema. |
| Número Esperado de Clientes na Fila ($L_q$) | $1000 \times 0,000132$ | $\approx 0,4344$ | Em média, há 0,4344 clientes esperando na fila. |
| Número Esperado de Clientes no Sistema ($L$) | $1000 \times 0,000435$ | $\approx 0,7373$ | O sistema tem, em média, 0,7373 clientes (fila + atendimento). |
| Número Médio de Servidores Ocupados ($c_{ocupados}$) | $0,303 \times 1$ | $\approx 0,303$ | Ocupação do único servidor. |

*Tabela 04: Parâmetros de desempenho utilizando GPU e um sistema M/M/1.*

