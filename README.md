# 🎯 SPIN Analytics Dashboard

Dashboard Streamlit para transformar reuniões de vendas em dados mensuráveis, usando a metodologia **SPIN Selling** como base analítica.

## 📋 Visão Geral

O objetivo desse projeto é **transformar reunião em dado mensurável**, identificando padrões que separam reuniões que avançam o funil das que ficam estagnadas.

### O que o dashboard faz:
- **SPIN Score** (0–10) para cada reunião
- **Correlação** com avanço no funil de vendas
- **Padrões** de comportamento de alta vs. baixa conversão
- **Nuvem de Palavras** dos termos mais usados nas negociações
- **Tabela de Frequência** de palavras de negócio
- **Recomendações estratégicas** adaptadas ao perfil real da equipe
- **Forecast Comercial** com cenário atual vs. cenário otimizado

---

## 🚀 Como Rodar

### Pré-requisitos

```bash
pip install streamlit pandas plotly wordcloud matplotlib
```

### Execução

```bash
streamlit run spin_dashboard.py
```

---

## 📁 Estrutura de Dados

### Modo Demo (GitHub)
O dashboard inclui `meetings_sample.json` com 20 reuniões fictícias para demonstração. Ao rodar sem apontar uma pasta válida de reuniões reais, o **Modo Demo** é ativado automaticamente.

### Modo Real (Produção)
O dashboard lê as pastas extraídas do MeetGeek no formato:

```
[base_dir]/
  out_meetgeek-001/
    out_meetgeek/
      meetings/
        [meeting_id]/
          metadata.json       ← Título da reunião
          summary.json        ← Resumo gerado pela IA
          transcript_sentences.jsonl  ← Transcrição parcial
          state.json          ← Duração e metadados
  out_meetgeek-002/
    ...
```

### Configuração no Dashboard
Na barra lateral, aponte o **Diretório Raiz** para a pasta que contém os `out_meetgeek-*`:

```
Diretório Raiz: C:/SuaPasta
```

---

## 🧠 Metodologia SPIN

| Dimensão | O que mede | Peso Máximo |
|----------|-----------|-------------|
| **S** - Situação | Contexto operacional do cliente | 2 pts |
| **P** - Problema | Dores e gargalos identificados | 3 pts |
| **I** - Implicação | Consequências da dor (multas, juros, riscos) | 3 pts |
| **N** - Need-Payoff | Solução declarada e benefícios esperados | 2 pts |

**SPIN Total: 0–10 pontos**

---

## 📊 Abas do Dashboard

| Aba | Conteúdo |
|-----|---------|
| 📊 Visão Geral | Métricas globais e radar SPIN sucesso vs fracasso |
| 🛠️ Análise Isolada | Tabela com score por reunião |
| 💡 Padrões | Comportamentos e gatilhos de conversão |
| ☁️ Nuvem | Word Cloud dos termos de negócio |
| 📋 Frequência | Contagem de palavras relevantes |
| 🎯 Recomendações | Plano de ação gerado dinamicamente |
| 📈 Forecast | Projeção de receita por cenário |

---

## ⚙️ Personalização

### Ajustar Keywords SPIN
No arquivo `spin_dashboard.py`, edite o dicionário `SPIN_KEYWORDS`:

```python
SPIN_KEYWORDS = {
    "S": ["contexto", "situação", "atualmente", ...],
    "P": ["problema", "dívida", "multa", ...],
    "I": ["consequência", "risco", "juros", ...],
    "N": ["solução", "investimento", "contrato", ...]
}
```

### Ajustar Gatilhos de Avanço
Edite a lista `NEXT_STEPS_KEYWORDS`:

```python
NEXT_STEPS_KEYWORDS = ["proposta", "contrato", "fechamento", ...]
```

---

## 📌 Observações Técnicas

- A transcrição do MeetGeek é **parcial** — o dashboard trata isso graciosamente
- Reuniões sem `summary.json` são processadas apenas via título e transcrição
- O sistema usa **heurística por palavras-chave**, não NLP avançado — rápido, transparente e ajustável

---

## 🏢 Sobre

Desenvolvido para o **Grupo Villela** como ferramenta de inteligência comercial baseada em dados de reuniões.
