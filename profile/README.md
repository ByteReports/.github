# ByteReports

> Aplicativo desktop para diagnóstico de hardware Windows — simples, didático e 100% local.

[![Plataforma](https://img.shields.io/badge/Plataforma-Windows%2010%2F11-blue)](https://github.com/ByteReports)
[![Linguagem Backend](https://img.shields.io/badge/Backend-Python-yellow)](https://github.com/ByteReports)
[![Linguagem Frontend](https://img.shields.io/badge/Frontend-React-61DAFB)](https://github.com/ByteReports)
[![Status](https://img.shields.io/badge/Status-Em%20desenvolvimento-orange)](https://github.com/ByteReports)

---

## Sumário

- [Sobre o Projeto](#sobre-o-projeto)
- [Equipe](#equipe)
- [Funcionalidades](#funcionalidades)
- [Tecnologias Utilizadas](#tecnologias-utilizadas)
- [Arquitetura](#arquitetura)
- [Estrutura do Projeto](#estrutura-do-projeto)
- [Requisitos do Sistema](#requisitos-do-sistema)
- [Roadmap](#roadmap)

---

## Sobre o Projeto

O **ByteReports** é um aplicativo desktop para Windows que realiza varreduras e diagnósticos nos principais componentes de hardware do computador, gerando relatórios claros e acessíveis voltados para usuários com pouco conhecimento técnico.

### Problema que resolve

Com base na pesquisa realizada pela equipe, **27% dos usuários de Windows** se consideram com conhecimento avançado para realizar correções em seus próprios computadores. Os softwares de diagnóstico disponíveis no mercado são ou excessivamente técnicos ou muito limitados. O ByteReports preenche essa lacuna traduzindo dados brutos de hardware em linguagem acessível para usuários com pouco conhecimento técnico, com recomendações práticas passo a passo.

### Diferenciais

| Atributo | Ferramentas tradicionais | ByteReports |
|---|---|---|
| Formato do dado | Valores brutos e métricas técnicas | Prescrições explicativas em linguagem simples |
| Dificuldade de uso | Requer conhecimento prévio | Nível iniciante a intermediário |
| Ação sugerida | Frequentemente inexistente | Recomendações passo a passo |
| Foco do relatório | Identificação de peças | Saúde, qualidade e melhoria |
| Privacidade | Variável | 100% local — nenhum dado é enviado para a internet |

---

## Equipe

Projeto desenvolvido no **1º semestre de 2026** durante a matéria de **Projeto Integrador III** do curso de Ciência da Computação do **UniCEUB — Asa Norte**, Brasília.

| Nome | Papel | Contato |
|---|---|---|
| Luiz Felipe Santos de Abreu | Product Owner · Frontend · Backend | github.com/OGUTAO |
| Guilherme Miranda Cavalcante | Scrum Master · Frontend · Backend | github.com/M1r40107 |
| José Waldo Saraiva Câmara Neto | Documentação · Backend | github.com/josewaldoneto |
| Bruno Monteiro Fonseca | Arquitetura de software · Backend · Frontend | github.com/BrunoMont18 |


**Orientação acadêmica:**
- Professora orientadora: Kadidja Valéria Reginaldo de Oliveira
- Stakeholder: Cleber Machado Ortiz

---

## Funcionalidades

### Análise de Hardware
- Varredura automática de CPU, RAM, armazenamento (HD/SSD/NVMe) e placa de vídeo
- Exibição gráfica de uso atual e capacidade dos componentes
- Identificação de nome comercial das peças

### Relatórios e Diagnósticos
- Classificação de severidade em três níveis com código de cores:
  - 🟢 **Saudável** — componente operando normalmente
  - 🟡 **Atenção** — situação que requer cuidado
  - 🔴 **Crítico** — problema que exige ação imediata
- Alerta automático quando HD/SSD possui menos de 10% de espaço livre

### Acessibilidade e Educação
- Textos explicativos sobre a função de cada componente, sem jargões técnicos
- Tooltips ao passar o mouse sobre siglas como CPU, RAM e SSD
- Modos claro e escuro
- Interface com contraste acessível para pessoas com daltonismo

### Exportação
- Exportação de relatório em **PDF**
- Exportação de relatório em **TXT**
- Dois modos de relatório: **Leigo** (linguagem acessível) e **Técnico** (dados detalhados)

### Notebooks
- Detecção automática de dispositivos portáteis
- Exibição do percentual da bateria

---

## Tecnologias Utilizadas

### Backend
- **Python** — lógica de negócio, coleta de dados e geração de relatórios
- **WMI (Windows Management Instrumentation)** — fonte primária de dados de hardware

### Frontend
... (126 linhas)
