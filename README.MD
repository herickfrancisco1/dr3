# 🎓 Agente Inteligente Planejador de Estudos (LangChain + Ollama)

Projeto desenvolvido para o **TP3** utilizando agentes inteligentes com raciocínio **ReAct**, **ferramentas customizadas (Tools)** e **memória conversacional** rodando 100% localmente via **Ollama**.

---

## 🎯 1. Descrição do Problema e da Solução

### O Problema
Estudantes universitários lidam simultaneamente com múltiplas disciplinas, cargas horárias distintas e prazos apertados. Gerenciar manualmente quanto estudar por dia e atualizar o progresso após cada sessão gera atrito e desorganização.

### A Solução
Um **Agente Inteligente de Estudos** baseado na arquitetura **ReAct** que atua como tutor de organização pessoal. Por meio de linguagem natural, o agente consulta a base de matérias do aluno, identifica prioridades, calcula metas diárias divididas em ciclos Pomodoro e atualiza o progresso concluído, lembrando do contexto da conversa.

---

## 🧪 2. Casos de Uso Testados e Resultados Observados

1. **Caso de Uso 1 — Consulta de Pendências (Uso de Tool):**
   - *Entrada:* `"Quais matérias eu tenho pendentes no momento?"`
   - *Ação ReAct:* O agente aciona `consultar_materias_pendentes()` e lista as disciplinas, destacando que *Inteligência Artificial* possui prioridade Alta (faltam 8h).
2. **Caso de Uso 2 — Cálculo de Meta com Referência Implícita (Memória + Tool):**
   - *Entrada:* `"Minha prova da matéria com prioridade alta é daqui a 4 dias. Quantas horas por dia preciso estudar?"`
   - *Ação ReAct:* Graças à memória conversacional (`MemorySaver`), o agente identifica que a matéria é *Inteligência Artificial* (8h restantes) e chama `calcular_meta_diaria(horas_restantes=8, dias_ate_prova=4)`, retornando `2.00 horas/dia` (5 ciclos Pomodoro).
3. **Caso de Uso 3 — Atualização de Estado (Memória + Tool de Escrita):**
   - *Entrada:* `"Acabei de estudar 2 horas dela! Pode registrar no meu progresso e me dizer quanto falta agora?"`
   - *Ação ReAct:* O agente mantém o contexto da disciplina e aciona `registrar_progresso_estudo(materia="Inteligência Artificial", horas_estudadas=2)`, confirmando que agora restam 6h.

---

## 🚀 3. Instruções para Execução

### Pré-requisitos
- Python 3.10+
- [Ollama](https://ollama.com/) instalado e em execução.

### Passo a passo
1. Clone este repositório:
   ```bash
   git clone <URL_DO_SEU_REPOSITORIO>
   cd <NOME_DA_PASTA>