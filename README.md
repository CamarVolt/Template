# Template CamarVolt

## Projeto:  
#### **Tomada medidora de gastos**

Versão 2.0                 
**Nome dos Integrantes da Equipe:** Gustavo Henrique, Ícaro Botelho, Maruan Biasi, Rafael Pereira, Ricardo Falção

---

## Histórico de Atualização

| Atividades            | Responsáveis | Data       | Observações                      |
|-----------------------|--------------|------------|----------------------------------|
| Adequação Template    | Camargo      | 03/09/2025 | Ajustes e Inserção do Contexto   |
| Entrega 1    | Equipe CamarVolt      | 10/09/2025 | Seção 1   |
| Entrega 2    | Equipe CamarVolt      | 24/09/2025 | Seções 2, 3 e 4   |

---

## Sumário

1. [Introdução](#1-introdução)  
   1.1 [Objetivo deste documento](#11-objetivo-deste-documento)  
   1.2 [Escopo do produto](#12-escopo-do-produto)  
   1.3 [Visão geral deste documento](#13-visão-geral-deste-documento)  
2. [Descrição geral do produto/protótipo](#2-descrição-geral-do-produtoprotótipo)  
3. [Contexto para Produto/Protótipo](#3-contexto-para-produtoprotótipo)  
4. [Requisitos do Produto/Protótipo](#4-requisitos-do-produtoprotótipo)  
5. [Artefatos do Produto/Protótipo](#5-artefatos-do-produtoprotótipo)  
6. [Considerações Finais](#6-considerações-finais)  
7. [Apêndices (evidências de Implementação)](#7-apêndices-evidências-de-implementação)  

---

## 1. Introdução

### 1.1 Objetivo deste documento
Este documento tem como objetivo apresentar a especificação e detalhamento do protótipo CamarVolt | Tomada medidora de gastos, um projeto de IOT. Serão descritos seus objetivos, escopo, funcionalidades e requisitos principais, de forma a orientar o desenvolvimento do dispositivo e sua integração com as camadas de software e hardware necessárias. A documentação visa servir como guia de referência tanto para a equipe de desenvolvimento quanto para validação acadêmica e técnica do projeto.

### 1.2 Escopo do produto
#### 1.2.1 Nome do produto/protótipo e de seus componentes principais
O produto é criado pela "Equipe CamarVolt" e se chama "Tomada medidora de gastos". Seus principais componentes são:
- Adaptador de tomada inteligente: Dispositivo físico que mede parâmetros elétricos relacionados ao consumo.
- Módulo de conectividade IoT: Microcontrolador responsável pela coleta, processamento inicial e envio dos dados para o servidor.
- Servidor: Software responsável por receber, armazenar e processar definitivamente os dados.
- Dashboard: Interface gráfica na web para visualização do consumo, relatórios e alertas.

#### 1.2.2 Missão do produto/protótipo
A missão do CamarVolt é proporcionar monitoramento acessível, confiável e em tempo real do consumo de energia elétrica em residências, auxiliando o usuário a compreender seus padrões de uso, identificar desperdícios e reduzir gastos. O protótipo busca facilitar o controle de consumo por meio de uma interface web fácil de utilizar, permitindo ao usuário maior conhecimento sobre seus gastos, possibilitando-o a tomar decisões mais conscientes sobre sua utilização de energia.

### 1.3 Visão geral deste documento
- Seção 2: apresenta-se a descrição geral do protótipo e de suas funcionalidades;

- Seção 3: é discutido o contexto do produto, incluindo ambiente de uso, público-alvo e restrições;

- Seção 4: encontram-se os requisitos funcionais, não funcionais, de hardware, software e plataformas;

- Seção 5: são descritos os artefatos do projeto, como diagramas e modelos;

- Seção 6: cada integrante da equipe apresenta suas considerações finais;

- Seção 7: são disponibilizadas evidências de implementação, como códigos e registros experimentais.

---

## 2. Descrição geral do produto/protótipo
A Tomada medidora de gastos é um protótipo IoT que coleta dados de tensão, corrente e potência, transmitindo-os via microcontrolador e wi-fi para um servidor central, que utilizando NodeJS, processa os dados, salvando-los em um banco de dados PostgreSQL

---

## 3. Contexto para Produto/Protótipo
O CamarVolt será constituído por dois elementos principais: o aparelho adaptador de tomada inteligente e o servidor de processamento e visualização de dados.

## Ambiente de uso

O aparelho será instalado diretamente em tomadas padrão brasileiro (2P+T), funcionando como um adaptador entre a tomada da parede e o dispositivo conectado.
O protótipo foi projetado para uso em residências, onde o monitoramento de consumo de energia elétrica é relevante.

## Usuários

Residenciais: moradores que desejam acompanhar e reduzir gastos de energia.

## Fluxo de interação

O aparelho adaptador coleta informações de corrente elétrica através do sensor ZMCT103C, processa localmente com o módulo Wemos ESP8266 e transmite os dados via rede Wi-Fi.
Os dados são enviados de forma segura para o servidor central, que pode estar hospedado localmente em um computador ou em uma plataforma em nuvem (AWS, Azure, Oracle, etc.).
O servidor recebe os dados, armazena-os em um banco de dados e processa os valores de consumo.
O dashboard web permite que os usuários visualizem consumo em tempo real, relatórios históricos e valores calculados de custo de energia.
Presets regionais (como tarifa de energia elétrica em Joinville) podem ser utilizados, além de valores customizados fornecidos pelo usuário.

## Restrições físicas e de design

O adaptador não deve ultrapassar 10 cm em profundidade nem 5 cm em largura/altura em relação à tomada.
O aparelho deve ser visualmente semelhante a adaptadores tradicionais, não podendo conter aparência ofensiva.
Materiais e design devem reduzir risco de fogo e evitar choques elétricos.

## Plataformas de desenvolvimento

Para prototipagem, serão utilizados equipamentos de soldagem, protoboard, cabos jumper e ferramentas de programação (ex.: VSCode + NodeJS).
O firmware será gravado no ESP8266 através de cabo USB e ambiente de desenvolvimento compatível (Arduino IDE ou PlatformIO).

## Segurança e confiabilidade

A comunicação entre aparelho e servidor deve ser criptografada.
O servidor deve tratar múltiplos dispositivos simultaneamente, sem perda ou desintegração de dados.
Tanto o aparelho quanto o servidor devem operar continuamente, utilizando apenas energia fornecida pela tomada (no caso do aparelho).

## Diagrama de Caso de Uso
<img width="713" height="398" alt="image" src="https://github.com/user-attachments/assets/116a8f1d-dc50-41ac-923b-0eb87a112de9" />

---

## 4. Requisitos do Produto/Protótipo
## Requisitos Funcionais (RF)

- RF01: Medir tensão, corrente, potência e fator de potência a cada 10 segundos.

- RF02: Calcular e armazenar o consumo total em kWh.

- RF03: Exibir gráficos e relatórios no dashboard.

- RF04: Gerar alertas em caso de sobrecarga ou consumo anormal.

- RF05: Permitir exportação dos dados em CSV/JSON.

- RF06: Conectar-se a redes Wi-Fi disponíveis.

- RF07: Enviar dados de consumo para o servidor central em tempo real.

- RF08: Calcular valores de gasto em energia elétrica a partir de custos inseridos pelo usuário.

- RF09: Oferecer presets de custo de energia elétrica (ex.: tarifa padrão de uma cidade).

- RF10: Medir correntes de até 30 amperes no máximo.

## Requisitos Não Funcionais (RNF)

- RNF01: O sistema deve ter disponibilidade mínima de 99%.

- RNF02: O tempo de resposta dos dados deve ser inferior a 5 segundos.

- RNF03: Todos os dados transmitidos devem ser criptografados (TLS).

- RNF04: O sistema deve armazenar dados históricos por pelo menos 12 meses.

- RNF05: O dispositivo não deve exceder 10 cm de protrusão da tomada (em ângulo reto).

- RNF06: O dispositivo não deve exceder 5 cm de protrusão nas direções paralelas à tomada.

- RNF07: O design deve inibir ou reduzir risco de incêndio e choques elétricos.

- RNF08: O dispositivo não pode ter aparência ofensiva nem nomes inadequados.

## Requisitos de Hardware

- Sensore de corrente: AC 30A SCT-013-030 Não Invasivo

- Módulo medidor de energia PZEM-004T.

- Microcontrolador ESP32 ou Wemos ESP8266 (CH340G).

- Fonte de alimentação estabilizada 5V 1A.

- Diodo de proteção.

- Protoboard para prototipação.

- Fios diversos e cabos jumper (macho-macho, macho-fêmea, fêmea-fêmea).

- Equipamentos de soldagem (ferro de solda, estanho, suporte com garras, EPI de segurança).

## Requisitos de Software

- Firmware em C++ (Arduino IDE / ESP-IDF).

- Node JS (processamento de dados e interface).

## Requisitos de Plataforma (IoT)

- Mesa para prototipação.

- Tomada elétrica padrão brasileiro (2P+T).

- Computador com acesso a IDE de programação (Arduino IDE / VSCode).

- Cabo USB para gravação do firmware.

- Ambiente de desenvolvimento com Node.js e VSCode.

## Requisitos de Plataforma (Servidor)

- Computador local dedicado ou instância em nuvem (AWS, Azure, Oracle, etc.).

## Diagrama de Hierarquia de Requisitos

![hierarquia_requisitosFINAL](https://github.com/user-attachments/assets/1daf5d86-589a-4c8b-8f8a-65bbb0314e46)

---

## 5. Artefatos do Produto/Protótipo

- **Visão de Usabilidade (aplicação mobile)** – Mockup (se necessário)  
- **Visão Arquitetural** – Arquitetura do Produto  
- **Visão Estrutural** – Diagrama de Blocos (IoT)  
- **Visão Comportamental** – Diagramas de Sequência ou Máquina de Estados ou Diagrama de Atividades  

---

## 6. Considerações Finais
<cada estudante integrante da equipe publica na entrada projeto as suas considerações finais a respeito da execução deste Projeto, como: lições aprendidas, importância do projeto, dificuldades encontradas, conhecimentos adquiridos> 

---

## 7. Apêndices (evidências de Implementação)
- Código Fonte do produto (link repositório remoto) ou trechos desse código  

---

📘 Engenharia de Software – Disciplina IoT  
S.I.A.S.
