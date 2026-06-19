## 🎯 Requisitos Atendidos

- [x] **Execução por push:** A pipeline é acionada automaticamente sempre que há novos commits nas branches principais.
- [x] **Execução manual:** Uso da trigger `workflow_dispatch` para permitir testes sob demanda via interface do GitHub.
- [x] **Execução agendada (schedule):** Pipeline configurada com cron job para rodar regressões noturnas.
- [x] **Geração de relatório de testes:** O framework de testes gera relatórios detalhados das execuções (HTML/XML).
- [x] **Armazenamento na pipeline (Artifacts):** Utilização do `actions/upload-artifact` para salvar e disponibilizar os relatórios para download.
- [x] **Uso do GitHub Actions:** Toda a infraestrutura foi montada em `.github/workflows`.

## 🛠️ Conceitos e Ferramentas Utilizadas

### 1. Integração Contínua (CI)
A Integração Contínua é uma prática de engenharia de software onde as alterações de código são integradas e validadas frequentemente. O benefício direto para **Quality Assurance (QA)** é o *Feedback Loop* rápido: bugs são identificados minutos após a submissão do código, evitando que falhas cheguem a ambientes de produção.

### 2. GitHub Actions
Ferramenta escolhida para orquestrar a pipeline. Ela permite definir **Workflows** (fluxos de trabalho automáticos), **Jobs** (conjunto de passos executados em um runner) e **Steps** (comandos individuais, como instalação e execução de testes).

### 3. Artifacts (Artefatos de Pipeline)
No contexto de QA, não basta a pipeline passar ou falhar, precisamos de evidências. Os **Artifacts** do GitHub Actions foram utilizados para capturar a pasta de relatórios gerada pelo framework de testes e anexá-la à execução. A condição `if: always()` foi aplicada de forma estratégica para garantir que o relatório seja salvo e disponibilizado para análise mesmo em caso de falha nos testes.

## 🚀 Como Executar

### Disparo Automático (Push)
1. Faça uma alteração no código.
2. Realize o commit e o push para a branch `main` ou `master`.
3. Acesse a aba **Actions** no repositório para acompanhar a execução.

### Disparo Manual
1. Acesse a aba **Actions** no repositório.
2. Selecione o workflow **Pipeline de Integração Contínua - QA** no menu esquerdo.
3. Clique no botão **Run workflow** e selecione a branch desejada.

## 📊 Como Acessar o Relatório de Testes

1. Acesse a aba **Actions** do GitHub.
2. Clique na última execução finalizada.
3. Role a página até a seção **Artifacts** (na parte inferior).
4. Clique em **relatorio-de-execucao** para baixar o arquivo compactado contendo as evidências e o relatório da automação.
