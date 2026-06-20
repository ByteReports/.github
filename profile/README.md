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
- **React** — interface gráfica do usuário

### Gestão e Ferramentas
- **GitHub** — controle de versão, gestão do projeto e documentação
- **Figma** — prototipação visual
- **Discord** — comunicação da equipe
- **Gemini / GitHub Copilot** — apoio ao desenvolvimento

---

## Arquitetura

O ByteReports adota uma **arquitetura em camadas** com execução 100% local na máquina do usuário.

```
┌─────────────────────────────────────────┐
│         Camada de Apresentação          │
│              (React - Frontend)         │
│  Telas: Início · Varredura · Relatório  │
└─────────────────┬───────────────────────┘
                  │ API local (HTTP)
┌─────────────────▼───────────────────────┐
│        Camada de Lógica de Negócio      │
│             (Python - Backend)          │
│ Diagnóstico · Classificação · Exportação│
└─────────────────┬───────────────────────┘
                  │
┌─────────────────▼───────────────────────┐
│         Camada de Coleta de Dados       │
│        (WMI - APIs nativas Windows)     │
│  CPU · RAM · Armazenamento · Bateria    │
└─────────────────────────────────────────┘
```

### Principais decisões arquiteturais

| Decisão | Justificativa |
|---|---|
| Execução 100% local | Garante privacidade total do usuário sem dependência de internet |
| Separação Frontend (React) e Backend (Python) | Permite evolução independente de cada camada |
| WMI como fonte primária | Infraestrutura nativa da Microsoft, garantindo confiabilidade |
| Empacotamento em executável único | Reduz barreira de instalação para usuários leigos |

### Fluxo de execução

1. Usuário abre o executável — interface React é carregada localmente
2. Ao clicar em **"Iniciar Análise do Sistema"**, o frontend envia requisição ao backend Python
3. Backend verifica se o serviço WMI está ativo; exibe erro claro caso negativo
4. Coleta de dados via WMI (limite máximo de 60 segundos)
5. Motor de diagnóstico aplica regras de classificação e gera o relatório
6. Relatório exibido na interface e salvo localmente para consulta futura
7. Usuário pode exportar em PDF ou TXT

---

## Estrutura do Projeto

```
ByteReports/repositories
├── ByteReports-backend/
│   ├── app.py                  # Inicializar backend
│   ├── bateria.py              # Módulo leitor de bateria
│   ├── cpu.py                  # Módulo leitor de cpu
│   ├── diagnostico.py          # Módulo gerador de sugestões e resumo da leitura
│   ├── disco.py                # Módulo leitor de disco
│   ├── gpu.py                  # Módulo leitor de gpu
│   ├── package-lock.py
│   ├── package.py
│   ├── placa_mae.py            # Módulo leitor de placa mãe
│   ├── ram.py                  # Módulo leitor de ram
│   ├── rede.py                 # Módulo leitor de uso de rede
│   ├── relatorio_teste.json
│   ├── sistema.py              # Módulo leitor de sistema operacional
│   └── utils.py
│
├── ByteReports-frontend/
│   ├── public/
│   └── src/
│       ├── assets/
│       ├── components/
│       ├── App.css
│       ├── App.jsx
│       ├── index.css
│       └── main.jsx
│
└── ByteReports-documentos/     # Repositório que contém todos os documentos do projeto
    └── Relatorios de sprint/
```

---

## Requisitos do Sistema

| Requisito | Mínimo |
|---|---|
| Sistema Operacional | Windows 10 ou Windows 11 |
| Arquitetura | 32 bits ou 64 bits |
| Serviço WMI | Ativo (necessário para a varredura) |
| Privilégios | Execução como Administrador |
| Conexão com internet | **Não necessária** — aplicativo 100% local |

---

## Roadmap

### Versão atual
- [x] Varredura de CPU, RAM e armazenamento
- [x] Relatório com classificação de severidade (Saudável / Atenção / Crítico)
- [x] Suporte a placas de vídeo integradas
- [x] Exportação em PDF
- [x] Exportação em TXT
- [x] Alerta de disco com menos de 10% de espaço livre
- [x] Tooltips explicativos
- [x] Textos explicativos sobre cada componente
- [x] Modo escuro e claro
- [x] Acessibilidade para daltonismo (modo de cores alternativo)

### Próximas versões (Projeto Integrador IV)
- [ ] Histórico de análises anteriores
- [ ] Detecção do Cycle Count e desgaste da bateria em notebooks
- [ ] Estimativa de vida útil dos componentes
- [ ] Suporte a placas de vídeo integradas

---

*Desenvolvido em Brasília — UniCEUB, 2026*
