---
{"dg-publish":true,"permalink":"/04-cadernos/2024-01-07-normas-aplicadas/","tags":["🧠️/📝️/🌱️"],"created":"2024-05-08T13:44:45.764-03:00","updated":"2024-01-10T14:59:46.560-03:00"}
---


***
| Relacionados |
| ------------ |

{ .block-language-dataview}
***

>[!multi-column]
>
>>[!abstract]+ Sobre
>>- Titulo da nota: `=this.file.title`
>>- Tipo: `INPUT[text:type]`
>>- Site: `INPUT[text:site]`
>>```meta-bind
INPUT[multiSelect(class(multiselectmin),option(🌱️, | 🌱️ | ), option(🌿️, | 🌿️ |), option(🌻, | 🌻 |), option(🌲️, | 🌲️ |), option(🌵, | 🌵 |)):evolucao]
>>```
>>```meta-bind
INPUT[multiSelect(class(multiselectmin1), option(🟥️), option(🟧️), option(🟨️), option(🟩️)):status]
>>```
>>>
>>
>>| ପ꒰ ˶• ༝ •˶꒱ଓ   🍃   `INPUT[toggle:dg-publish]`
>> 
>
>
>>[!hint]+ E aí?
>>🧠️/📝️/🌱️
>>
>>
>>```meta-bind
INPUT[select(option(📥️/🐦️/🟩️, 🎆 Arquivar )):tags]
>>```
>>
>>```meta-bind
INPUT[multiSelect(class(multiselecttemas),option(Conservação-Restauração, 🏺 CR 🏺 ), option(Programação, 👨🏻‍💻 PC 👨🏻‍💻), option(Divulgação Cientifica, ⚗️ DC ⚗️ ), option(Comunicação, 🦜 Social 🦜), option(Neurodivergência, 🌈 PCD 🌈), option(Pessoal, 🦝 Eu 🦝)):tema]
>>```
>>>
>>```meta-bind
INPUT[list(class(multiselecttemas)):keywords]
>>```
***

# 2024-01-07 - Normas aplicadas

<small>2024-01-07 | 2024-01-10T14:59:00.000-03:00</small>

![Pasted image 20240103170036.jpg](/img/user/XX.%20Anexos/Pasted%20image%2020240103170036.jpg)

![Pasted image 20240103170218.jpg](/img/user/XX.%20Anexos/Pasted%20image%2020240103170218.jpg)
![Pasted image 20240103170335.jpg](/img/user/XX.%20Anexos/Pasted%20image%2020240103170335.jpg)

![Pasted image 20240103170413.jpg](/img/user/XX.%20Anexos/Pasted%20image%2020240103170413.jpg)
![Pasted image 20240103170424.jpg](/img/user/XX.%20Anexos/Pasted%20image%2020240103170424.jpg)

***

### Folhas de caderno com o mesmo tema

``` dataview
table  status AS "Status", keywords AS "Palavras-Chave", created AS "Criado em:"
from "04. Cadernos"
where tema = this.tema 
where titulo != "this.titulo"
sort updated DESC
LIMIT 10
```

### Relacionadas?

| File                                                                                                                                                                                                                                               | Autor                                 | Tema                                      | Tags                          | Palavras-Chave                                               |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------- | ----------------------------------------- | ----------------------------- | ------------------------------------------------------------ |
| [[02. Feed/2024-01-14 - How to Manage Tasks in Obsidian\|2024-01-14 - How to Manage Tasks in Obsidian]]                                                                                                                                         | \-Tim Miller                          | <ul><li>Programação</li></ul>             | <ul><li>📥️/📰️/🟥️</li></ul> | <ul><li>obsidian</li><li>meuSetup</li><li>dataview</li></ul> |
| [[02. Feed/2024-01-14 - Import social media accounts into Obsidian Plugin\|2024-01-14 - Import social media accounts into Obsidian Plugin]]                                                                                                     | \-                                    | <ul><li>Programação</li></ul>             | <ul><li>📥️/📰️/🟥️</li></ul> | <ul><li>obsidian</li><li>meuSetup</li><li>Difusão</li></ul>  |
| [[02. Feed/2024-01-14 - Obsidian for Documenting Memories\|2024-01-14 - Obsidian for Documenting Memories]]                                                                                                                                     | \-adityavikram surana                 | <ul><li>Programação</li></ul>             | <ul><li>📥️/📰️/🟥️</li></ul> | <ul><li>meuSetup</li><li>obsidian</li><li>Galeria</li></ul>  |
| [[02. Feed/2024-01-14 - Promnesia\|2024-01-14 - Promnesia]]                                                                                                                                                                                     | \-                                    | <ul><li>Programação</li></ul>             | <ul><li>📥️/📰️/🟥️</li></ul> | <ul><li>meuSetup</li><li>Web</li></ul>                       |
| [[02. Feed/2024-01-15   -  How I Set Up My AI-Powered Second Brain in Obsidian (ChatGPT, Search, Assistant, Plugins, Tools)\|2024-01-15   -  How I Set Up My AI-Powered Second Brain in Obsidian (ChatGPT, Search, Assistant, Plugins, Tools)]] | John Mavrick\-                        | <ul><li>Programação</li></ul>             | <ul><li>📥️/🎥️/🟥️</li></ul> | <ul><li>meuSetup</li><li>obsidian</li></ul>                  |
| [[02. Feed/2024-01-15 - An AI copilot for your second brain\|2024-01-15 - An AI copilot for your second brain]]                                                                                                                                 | \-khoj-ai                             | <ul><li>Programação</li></ul>             | <ul><li>📥️/📰️/🟥️</li></ul> | <ul><li>obsidian</li><li>meuSetup</li></ul>                  |
| [[02. Feed/2024-01-15 - Easy Exports to Academic Templates\|2024-01-15 - Easy Exports to Academic Templates]]                                                                                                                                   | \-Soft-Material3294                   | <ul><li>Programação</li></ul>             | <ul><li>📥️/📰️/🟥️</li></ul> | <ul><li>meuSetup</li></ul>                                   |
| [[02. Feed/2024-01-15 - HelpMate for Obsidian\|2024-01-15 - HelpMate for Obsidian]]                                                                                                                                                             | \-TfTHacker                           | <ul><li>Programação</li></ul>             | <ul><li>📥️/📰️/🟥️</li></ul> | <ul><li>meuSetup</li><li>obsidian</li></ul>                  |
| [[02. Feed/2024-01-16 - Compile many Obsidian notes down to one\|2024-01-16 - Compile many Obsidian notes down to one]]                                                                                                                         | \-mgmeyers                            | <ul><li>Programação</li></ul>             | <ul><li>📥️/📰️/🟥️</li></ul> | <ul><li>obsidian</li><li>meuSetup</li></ul>                  |
| [[02. Feed/2024-01-17 - undefined\|2024-01-17 - undefined]]                                                                                                                                                                                     | \-%author%                            | <ul><li>Programação</li></ul>             | <ul><li>📥️/📰️/🟥️</li></ul> | <ul><li>aí prompts</li></ul>                                 |
| [[02. Feed/2024-01-19 - Monotropism, Young People and Autistic Burnout\|2024-01-19 - Monotropism, Young People and Autistic Burnout]]                                                                                                           | \-Helen Edgar                         | <ul><li>Neurodivergência</li></ul>        | <ul><li>📥️/📰️/🟥️</li></ul> | <ul></ul>                                                    |
| [[02. Feed/2024-01-19 - undefined\|2024-01-19 - undefined]]                                                                                                                                                                                     | \-4 Jan
Written By Ann Memmott PgC MA | <ul><li>Neurodivergência</li></ul>        | 📥️/📰️/🟥️                   | <ul></ul>                                                    |
| [[02. Feed/2024-01-20 - lattes\|2024-01-20 - lattes]]                                                                                                                                                                                           | \-                                    | <ul><li>Conservação-Restauração</li></ul> | 📥️/📰️/🟥️                   | <ul></ul>                                                    |
| [[02. Feed/2024-02-02 - undefined\|2024-02-02 - undefined]]                                                                                                                                                                                     | \-Jesse Meadows                       | <ul><li>Neurodivergência</li></ul>        | <ul><li>📥️/📰️/🟥️</li></ul> | <ul><li>neurodiversidade</li></ul>                           |
| [[02. Feed/Basic OCR in Obsidian\|Basic OCR in Obsidian]]                                                                                                                                                                                       | \-                                    | <ul><li>Programação</li></ul>             | <ul><li>📥️/📰️/🟥️</li></ul> | <ul><li>obsidian</li><li>meuSetup</li></ul>                  |
| [[02. Feed/Instructors are learners too Making faculty development accessible to faculty\|Instructors are learners too Making faculty development accessible to faculty]]                                                                       | \-Sarah Silverman                     | <ul><li>Neurodivergência</li></ul>        | <ul><li>📥️/📰️/🟥️</li></ul> | <ul><li>neurodiversidade</li></ul>                           |
| [[02. Feed/NEURODIVERSITY SOME BASIC TERMS & DEFINITIONS • NEUROQUEER\|NEURODIVERSITY SOME BASIC TERMS & DEFINITIONS • NEUROQUEER]]                                                                                                             | \-                                    | <ul><li>Neurodivergência</li></ul>        | <ul><li>📥️/📰️/🟥️</li></ul> | <ul><li>neurodiversidade</li></ul>                           |

{ .block-language-dataview}

***