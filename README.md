# 🏥 Saúde Simples

Sistema simples de gestão de clínica, feito em **Java** e executado no terminal. Cadastra pacientes, médicos e salas, agenda consultas sem conflito de horário e controla uma fila de espera.

## 📌 Problema

Clínicas costumam ter marcações duplicadas, salas de espera cheias e dificuldade para saber quem está disponível. O Saúde Simples impede conflitos de horário entre paciente, médico e sala e organiza a fila de atendimento.

Fonte: [Revista Master](https://revistamaster.emnuvens.com.br/RM/article/download/802/385)

**Usuários:** recepcionista, secretário(a) e administrador da clínica.

## ✨ Funcionalidades

- Cadastrar, listar, pesquisar, editar e desativar pacientes
- Cadastrar médicos e salas
- Agendar, listar (por data), concluir e cancelar consultas
- Fila de espera (entrar e atender)
- Indicadores: média de idade, total de consultas, maior idade, ranking de médicos e pessoas na fila
- Exportar pacientes para CSV
- Salvar paciente no banco H2

## 📏 Regras de negócio

1. Paciente, médico e sala precisam existir para agendar.
2. Paciente inativo não recebe consultas nem entra na fila.
3. Médico indisponível não recebe consultas.
4. Paciente, médico e sala não podem ter duas consultas no mesmo horário (consultas canceladas não contam).
5. Só é possível concluir uma consulta agendada.
6. Uma consulta já realizada não pode ser cancelada.
7. Um paciente não entra duas vezes na fila.
8. Ao agendar, a sala fica ocupada. Ao concluir ou cancelar a consulta, ela volta a ficar livre.

Quando uma regra é violada, o sistema mostra `ERRO: ...` e continua funcionando.

## 🧱 Classes

| Classe | Função |
|---|---|
| `Paciente`, `Medico`, `Sala` | Dados de cada pessoa ou local |
| `Consulta` | Liga paciente, médico e sala a uma data (`AGENDADA`, `REALIZADA` ou `CANCELADA`) |
| `FilaEspera` | Lista de pacientes aguardando |
| `Clinica` | Guarda tudo e aplica as regras de negócio e os indicadores |
| `Main` | Menu do terminal |
| `Banco` | Salva paciente no H2 (JDBC) |
| `CSV` | Exporta pacientes para `data/pacientes.csv` |

## 🛠️ Tecnologias

- Java 21
- Maven
- H2 Database (banco em arquivo, sem instalação)
- JUnit 5 (testes)

## 🚀 Como executar

Pré-requisitos: **JDK 21** e **Maven** instalados (confira com `java -version` e `mvn -version`).

```bash
git clone <url-do-repositorio>
cd SaudeSimples
mvn test
```

Para rodar o programa, abra a pasta numa IDE (IntelliJ, Eclipse ou VS Code) e execute a classe `saude.Main`.

> Execute sempre a partir da pasta que contém o `pom.xml`. Os arquivos gerados ficam na pasta `data/`.

## 🧪 Testes

O `ClinicaTest` verifica duas coisas: uma segunda consulta no mesmo horário é recusada, e a sala fica ocupada ao agendar e livre ao concluir ou cancelar.

## 📁 Estrutura

```
SaudeSimples/
├── pom.xml
└── src/
    ├── main/java/saude/   (Main, Clinica, Paciente, Medico, Sala,
    │                       Consulta, FilaEspera, Banco, CSV)
    └── test/java/saude/   (ClinicaTest)
```

## ⚠️ Limitações

- Os dados ficam em memória e são perdidos ao fechar o programa. O H2 só guarda os pacientes salvos pela opção do menu, e eles não são recarregados.
- Os IDs são digitados pelo usuário, sem verificação de duplicados.
- A situação da sala (ocupada/livre) é só informativa e não impede novos agendamentos em outros horários.

## 🤖 Uso de IA

| Ferramenta | Objetivo | Resumo do uso | Revisão pelo Dev |
|---|---|---|---|
| ChatGPT | Código base e documentação | Estrutura inicial, classes, regras de negócio, menu e README. | Código e regras testados e revisados pelos integrantes. |
| Claude | Revisão e documentação | Correção de erros de ambiente (Maven e CSV), ajuste da regra da sala e reescrita do README. | Conteúdo conferido com o código-fonte. |
