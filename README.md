# 🧠 Miniguia de Estudos com NotebookLM — Engenharia de Prompt para LLMs

> Caderno Temático construído com Inteligência Artificial (NotebookLM / Gemini) como ferramenta de aprendizagem ativa, unindo pensamento crítico, curadoria de fontes e organização do conhecimento.

![Status](https://img.shields.io/badge/status-conclu%C3%ADdo-brightgreen)
![Tema](https://img.shields.io/badge/tema-Engenharia%20de%20Prompt-blue)
![Ferramenta](https://img.shields.io/badge/ferramenta-NotebookLM-orange)

---

## 📌 1. Contexto e Objetivos

**Assunto escolhido:** Engenharia de Prompt para LLMs (Large Language Models).

A Engenharia de Prompt é a disciplina que estuda como estruturar instruções para modelos de linguagem de forma a obter respostas mais precisas, seguras e reutilizáveis. Escolhi este tema por ser a base de qualquer aplicação prática de IA generativa e por conectar habilidades técnicas (estruturação de prompts, RAG) com preocupações de segurança e governança (OWASP, NIST).

### 🎯 Objetivos de estudo

- Entender **as principais técnicas de prompting** e quando aplicar cada uma.
- Diferenciar boas práticas de estruturação (papéis, delimitadores, XML/Markdown, few-shot).
- Compreender os **riscos de segurança** associados a LLMs (ex.: Prompt Injection — OWASP Top 10 for LLM).
- Relacionar prompts a **frameworks de governança e gestão de risco** (NIST AI RMF).
- Consolidar um **miniguia reutilizável** para revisões futuras.

---

## 📚 2. Curadoria de Fontes

Foram selecionadas e carregadas **5 fontes abertas** no NotebookLM, combinando pesquisa acadêmica, documentação oficial de provedores e frameworks de segurança:

| # | Fonte | Tipo | Foco |
|---|-------|------|------|
| 1 | **A Systematic Survey of Prompt Engineering in LLMs: Techniques and Applications** — arXiv:2402.07927 | Paper acadêmico | Panorama das técnicas de prompting |
| 2 | **AI Risk Management Framework (AI RMF)** — NIST | Framework / PDF | Gestão de risco em IA e infraestrutura crítica |
| 3 | **Introduction to prompting** — Google Cloud Documentation (Gemini) | Documentação oficial | Boas práticas de prompt design |
| 4 | **OWASP Top 10 for Large Language Model Applications** — OWASP Foundation | Framework de segurança | Riscos de segurança em LLMs |
| 5 | **Prompt engineering** — OpenAI API | Documentação oficial | Estratégias e táticas de prompt |

### 🔗 Links das fontes

1. A Systematic Survey of Prompt Engineering — https://arxiv.org/abs/2402.07927
2. NIST AI Risk Management Framework — https://www.nist.gov/itl/ai-risk-management-framework
3. Google Cloud — Introduction to prompting — https://cloud.google.com/vertex-ai/generative-ai/docs/learn/prompts/introduction-prompt-design
4. OWASP Top 10 for LLM Applications — https://owasp.org/www-project-top-10-for-large-language-model-applications/
5. OpenAI — Prompt engineering — https://platform.openai.com/docs/guides/prompt-engineering

---

## 🧪 3. Engenharia de Prompts e "Cicatrizes"

Esta seção documenta o **raciocínio por trás dos resultados**: os prompts estratégicos testados no NotebookLM, as variações e as dificuldades reais encontradas (*troubleshooting*).

### 3.1. Perguntas estratégicas testadas

| Prompt | Objetivo | Resultado obtido |
|--------|----------|------------------|
| *"Com base apenas nas fontes carregadas, liste as técnicas de prompting citadas. Para cada uma: definição em 1 frase, quando usar e a fonte de origem."* | Extração estruturada + rastreabilidade | Excelente. Gerou tabela com técnicas (Zero-shot, Few-shot, Role-prompting, CoT, RAG) já citando as fontes. |
| *"Quais são os principais riscos de segurança no OWASP Top 10?"* | Aprofundar segurança | Bom. Destacou Prompt Injection como risco central e citou a fonte OWASP. |
| *"O que o NIST propõe para gerenciar riscos em infraestrutura crítica?"* | Conectar governança | Bom, mas exigiu reforço de escopo (ver cicatriz #2). |
| *"Como usar tags XML e Markdown para estruturar prompts eficazes?"* | Boas práticas de formatação | Bom. Sintetizou uso de delimitadores das docs Google/OpenAI. |
| *"Explique Retrieval-Augmented Generation (RAG): definição, quando usar e fonte."* | Técnica avançada | Muito bom. Definiu RAG como injeção de contexto externo no momento da consulta. |

### 3.2. Variações de prompt testadas

- **Genérico → Ancorado nas fontes:** trocar *"Explique engenharia de prompt"* por *"Com base APENAS nas fontes carregadas, explique..."* reduziu drasticamente respostas genéricas e forçou citações.
- **Aberto → Formato definido:** pedir *"em forma de tabela com colunas: definição / quando usar / fonte"* deixou a saída muito mais reutilizável do que texto corrido.
- **Amplo → Fatiado:** dividir "resuma tudo" em perguntas menores por fonte melhorou a precisão e a rastreabilidade das citações.

### 3.3. Cicatrizes / Troubleshooting (o que deu errado e como resolvi)

1. **Respostas genéricas demais:** prompts amplos faziam o modelo responder com conhecimento geral, sem usar as fontes. **Solução:** ancorar sempre com *"com base apenas nas fontes carregadas"* e pedir a citação da origem.
2. **Perda de escopo em temas transversais:** ao perguntar sobre NIST, o modelo misturava conceitos gerais de risco. **Solução:** restringir o recorte (*"...aplicado a infraestrutura crítica, segundo o AI RMF"*).
3. **Falta de rastreabilidade:** nas primeiras tentativas as respostas não indicavam de qual fonte vinham. **Solução:** exigir explicitamente "cite a fonte de origem de cada item".
4. **Saída difícil de reaproveitar:** texto corrido dificultava o estudo. **Solução:** padronizar formato de saída (tabelas, listas, "definição em 1 frase").

---

## 📖 4. Miniguia de Estudo (Entrega Final)

### 4.1. Resumos estruturados

**O que é Engenharia de Prompt**
Prática de projetar e refinar instruções para orientar o comportamento de LLMs, essencial em tarefas complexas onde entradas simples não bastam. Em produção, recomenda-se tratar prompts como **código versionado**, permitindo testes e avaliações sistemáticas antes de implementá-los.

**Principais técnicas**
- **Zero-shot:** instrução direta, sem exemplos. Rápido para tarefas simples.
- **Few-shot:** inclui exemplos no prompt para guiar o formato/estilo da resposta.
- **Role-prompting:** define uma identidade/papel (ex.: "você é um especialista em segurança") para dar prioridade a regras de negócio ou segurança sobre as entradas do usuário.
- **Chain-of-Thought (CoT):** induz o raciocínio passo a passo, melhorando tarefas de lógica.
- **RAG (Retrieval-Augmented Generation):** injeta informação externa e relevante no prompt no momento da consulta, útil para dados proprietários, privados ou muito recentes.

**Boas práticas de estruturação**
Usar delimitadores claros (**XML/Markdown**) para separar instrução, contexto e dados; ser específico sobre o formato de saída; e fornecer contexto suficiente.

**Segurança e governança**
- **OWASP Top 10 for LLM:** destaca a **Prompt Injection**, em que entradas maliciosas manipulam o modelo para acessar dados protegidos ou desviar de restrições éticas e de segurança.
- **NIST AI RMF:** oferece um framework para **governar, mapear, medir e gerenciar** riscos de sistemas de IA.

### 4.2. Glossário

| Termo | Definição |
|-------|-----------|
| **LLM** | Large Language Model — modelo de linguagem treinado em grandes volumes de texto para gerar e compreender linguagem natural. |
| **Prompt** | Instrução/entrada fornecida ao modelo para obter uma resposta. |
| **Engenharia de Prompt** | Disciplina de projetar e otimizar prompts para respostas precisas, seguras e reutilizáveis. |
| **Zero-shot** | Prompt sem exemplos; o modelo responde apenas com a instrução. |
| **Few-shot** | Prompt com exemplos que guiam o formato/estilo da resposta. |
| **Role-prompting** | Atribuição de um papel/persona ao modelo para orientar o comportamento. |
| **Chain-of-Thought (CoT)** | Técnica que induz raciocínio passo a passo. |
| **RAG** | Retrieval-Augmented Generation — adiciona contexto externo relevante ao prompt na hora da consulta. |
| **Prompt Injection** | Ataque em que entradas maliciosas manipulam o comportamento do LLM. |
| **Delimitadores (XML/Markdown)** | Marcações que separam instrução, contexto e dados dentro do prompt. |
| **NIST AI RMF** | Framework do NIST para gestão de riscos de IA. |
| **OWASP Top 10 for LLM** | Lista dos 10 principais riscos de segurança em aplicações com LLMs. |
| **Grounding** | Ancorar a resposta do modelo em fontes/dados confiáveis. |

### 4.3. Prompts reutilizáveis para revisões futuras

```text
1. EXTRAÇÃO ANCORADA
"Com base APENAS nas fontes carregadas, liste os principais conceitos sobre <TEMA>.
Para cada um: definição em 1 frase, quando usar e a fonte de origem."

2. COMPARAÇÃO
"Compare <TÉCNICA A> e <TÉCNICA B> segundo as fontes, em uma tabela com colunas:
definição, vantagens, limitações e quando usar. Cite a fonte de cada linha."

3. REVISÃO RÁPIDA (FLASHCARDS)
"Gere 10 perguntas e respostas curtas (flashcards) sobre <TEMA>, usando apenas as fontes.
Ordene do conceito mais básico ao mais avançado."

4. FOCO EM SEGURANÇA
"Liste os riscos de segurança relacionados a <TEMA> segundo o OWASP Top 10 for LLM.
Para cada risco: descrição, exemplo e mitigação."

5. RESUMO EXECUTIVO
"Faça um resumo executivo de até 200 palavras sobre <TEMA>, apenas com base nas fontes,
destacando os 3 pontos mais importantes para um iniciante."

6. VERIFICAÇÃO DE ESCOPO
"Responda <PERGUNTA> considerando SOMENTE o que está nas fontes carregadas.
Se a informação não estiver nas fontes, diga explicitamente 'não consta nas fontes'."
```

---

## 🚀 Como este projeto foi construído

1. Definição do tema e dos objetivos de estudo.
2. Curadoria e upload de 5 fontes abertas no **NotebookLM**.
3. Engenharia e teste iterativo de prompts, registrando respostas e dificuldades.
4. Consolidação do miniguia (resumos, glossário e prompts reutilizáveis).
5. Documentação de tudo neste repositório como parte do portfólio.

---

## 🛠️ Ferramentas utilizadas

- **NotebookLM (Google / Gemini)** — caderno temático e análise das fontes.
- **GitHub** — versionamento e portfólio.
- **Markdown** — estruturação da documentação.

---

> 📎 Projeto desenvolvido como Desafio de Projeto da **DIO** — uso da IA como ferramenta de aprendizagem ativa.
