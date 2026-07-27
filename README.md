# Controle de Devolução e Movimentação de Equipamentos

Sistema de controle de entrega e devolução de equipamentos (roteadores, ONTs/ONUs, repetidores) para técnicos de campo em uma operação de provedor de internet, desenvolvido em Excel com automação por fórmulas.

> ⚠️ **Nota sobre os dados:** todos os nomes, códigos de técnico, números de série e documentos usados neste projeto são **fictícios**, gerados apenas para demonstração. A estrutura e a lógica são baseadas em um sistema real que desenvolvi no meu ambiente de trabalho, mas nenhum dado real de colaboradores, clientes ou da empresa é exibido aqui.

## Contexto e problema

Em operações de campo (instalação/manutenção de internet), cada técnico recebe equipamentos do depósito para instalar em clientes. Sem controle, é difícil saber:
- Quanto equipamento cada técnico tem em mãos
- Quais equipamentos já foram entregues a clientes (e por isso saíram do controle do depósito, pendentes de eventual devolução/RMA)
- O histórico completo de um número de série específico
- Quais técnicos estão com mais pendência de devolução

Esse sistema resolve isso substituindo controle manual/disperso por uma planilha única, auditável e com consultas automáticas.

## O que o sistema faz

- **Cadastro de técnicos** com geração automática de código de depósito
- **Registro de movimentações** (entrega de equipamento por técnico, com número de série, data, documento e observação)
- **Consulta dinâmica** por técnico e período, por equipamento, ou por número de série individual — trazendo tanto a situação atual quanto o histórico completo
- **Dashboard** com volume de entregas por técnico em um período selecionável
- **Ranking de pendências**: técnicos com mais equipamentos entregues diretamente a clientes (aguardando devolução/logística reversa)
- **Comprovante de devolução** gerado automaticamente por técnico e data
- **Normalização de nomes**: uma tabela de "apelidos" resolve variações no registro do nome do mesmo técnico ao longo do tempo (ex.: mudança de empresa terceirizada, nome digitado de forma diferente), evitando que o mesmo profissional apareça como pessoas distintas nas consultas

## Estrutura da planilha

| Aba | Função |
|---|---|
| `Técnicos` | Cadastro de técnicos e geração automática do código de depósito |
| `Controle de Entrega` | Registro de todas as movimentações (linha a linha) |
| `Consulta` | Consulta cruzada por técnico/período, equipamento ou nº de série |
| `Dashboard` | Visão consolidada de entregas por período |
| `Ranking Clientes` | Ranking de equipamento pendente de devolução por técnico |
| `Comprovante DEV` | Geração de comprovante de devolução por técnico/data |
| `Catálogo_Itens` | Base de referência dos modelos de equipamento |
| `Apelidos_Tecnico` | Tabela de normalização de nomes de técnico |

## Técnicas aplicadas

- Fórmulas condicionais e de agregação: `SUMIFS`, `COUNTIFS`, `INDEX`/`MATCH`, `VLOOKUP`, `IFERROR`
- Geração automática de código a partir de texto (`MID`, `LEN`, concatenação)
- Normalização de dados via tabela auxiliar de "de-para" (nome histórico → nome canônico)
- Separação entre dados brutos (`Controle de Entrega`), regras de negócio (fórmulas) e camadas de consulta/visualização (Dashboard, Ranking, Comprovante)

## Sobre este projeto

Este é um sistema que desenvolvi como teste de desenvolvimento facilitando meu trabalho como atual Supervisor de Logística, aplicando minha experiência de 10+ anos em operações industriais para estruturar um controle que antes era feito de forma manual/dispersa. Hoje em transição para Análise/Engenharia de Dados, uso esse tipo de projeto para aplicar modelagem de dados, automação e lógica de consulta em um problema de negócio real.

**Autor:** Alexandre Baldoino
[LinkedIn](https://www.linkedin.com/in/alexandrebaldoino) · [GitHub](https://github.com/alexderik)
