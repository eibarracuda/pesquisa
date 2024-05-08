---
{"dg-publish":true,"permalink":"/05-projetos/redede-museus/arquivo-de-demandas-gerais/reunioes-de-articulacao-entre-a-equipe-internas-e-externas-memoria-2023/","tags":["💼/📝️/🟧️"],"created":"2024-02-04T09:31:47.921-03:00","updated":"2024-02-14T13:07:34.072-03:00"}
---


>[!multi-column]
>>[!Info]
>> - Tags: `INPUT[suggester(defaultValue(💼/📝️/🟥️),option(💼/📝️/🟥️, 🟥️), option(💼/📝️/🟧️, 🟧️), option(💼/📝️/🟨️, 🟨️), option(💼/📝️/🟩️, 🎆 Arquivar)):tags]`
>
>>[!tldr]
>> ```meta-bind
INPUT[multiSelect(class(multiselect), option(🟩️), option(🟨️), option(🟧️), option(🟥️), option(⛔)):status]
>> ```
>
>> [!warning]+ 📍 Espaço
>> ```meta-bind
INPUT[[class(multiselect), option([Herbário Norte Mineiro](Herbário Norte Mineiro.md|multiSelect(class(multiselect), option([Herbário Norte Mineiro]], | MCCA |), option([[Centro de Memória da Escola de Enfermagem.md]], | CEMENF |), option([[CEMEMOR]], | CEMEMOR |), option([[Centro de Memória da Odontologia.md]], | CMO |), option([[Centro de Pesquisa, Memória e Documentação da Faculdade de Educação]], | CEDOC-FaE |), option([[Museu da Matemática.md]], | MuMat |), option([[Núcleo Técnico Científico da Rede.md]], | Rede |), option([[GT Divulgação Científica.md]], | GEDIC |)):espaco]
>>```
>

## Calendário do Grupo de Trabalho

Esta ferramenta visa set uma plataforma de colaboração, divisão de tarefas e registro de atividades.
Todos os bolsistas tem permissão de agendar eventos ou reuniões, convidar participantes, etc. É incentivado que todos os eventos sejam agendados nesta plataforma, ou registrados posteriormente como forma de controle.

## Métodos

Para gerar este relatório foi usado um script para *google sheets,* exportado em.csv e agregados para visualização abaixo.
No inicio do próximo semestre se planeja uma análise do trabalho alcançado e planejamento para adequação de ações futuras.

Código usado:

```
function importarEventosCalendario() {
  // ID do seu calendário do Google
  var idCalendario = '6c17a44b4eb49b8ffa62c534e5f20d1891d336c44e3af4f77db25855e77afcb5@group.calendar.google.com';

  // Obter a instância do calendário
  var calendario = CalendarApp.getCalendarById(idCalendario);

  // Definir a data inicial para 1º de janeiro de 2023
  var dataInicial = new Date('2023-01-01T00:00:00Z');

  // Definir a data final para 31 de dezembro de 2023
  var dataFinal = new Date('2023-12-31T23:59:59Z');

  // Obter os eventos do calendário
  var eventos = calendario.getEvents(dataInicial, dataFinal);

  // Referência à planilha ativa
  var planilha = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();

  // Limpar a planilha antes de adicionar novos eventos
  planilha.clear();

  // Adicionar cabeçalhos, incluindo novas colunas para participantes e link da videochamada
  planilha.appendRow(["Título", "Data", "Hora de Início", "Localização", "Descrição", "Participantes", "Link da Videochamada"]);

  // Iterar sobre eventos e adicionar à planilha
  for (var i = 0; i < eventos.length; i++) {
    var evento = eventos[i];
    var titulo = evento.getTitle();
    var dataInicio = evento.getStartTime().toLocaleDateString();
    var horaInicio = evento.getStartTime().toLocaleTimeString();
    var localizacao = evento.getLocation();
    var descricao = evento.getDescription();

    // Obter participantes e link da videochamada
    var participantes = evento.getGuestList().map(function(guest) {
      return guest.getEmail();
    });
   
    // Adicionar linha à planilha
    planilha.appendRow([titulo, dataInicio, horaInicio, localizacao, descricao, participantes.join(', ')]);
  }
}

```

## Lista de reuniões realizadas em 2023/02

<center><iframe width="560" height="700" src="https://drive.google.com/file/d/1NCPbd6qRdQEusXCtebwHyVjIxxi58HI4/view?usp=sharing"></iframe></center>
![rodapeprojeto.png](/img/user/XX.%20Anexos/rodapeprojeto.png)
