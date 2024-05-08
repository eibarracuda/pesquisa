---
{"dg-publish":true,"permalink":"/04-cadernos/2024-01-07-configuracoes-highlighter-para-vicious/","tags":["🧠️/📝️/🌲️"],"created":"2024-01-07T12:12:17.873-03:00","updated":"2024-02-16T13:07:28.312-03:00"}
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
>>- Tempo de maturação desta ideia:
>>```meta-bind
INPUT[inlineSelect(class(multiselectmin), defaultValue(🌱️), option(🌱️, | 🌱️ |), option(🌿️, | 🌿️ |), option(🌻, | 🌻 |), option(🌲️, | 🌲️ |), option(🌵, | 🌵 |)):evolucao]
>>```
>>- Status:
>>```meta-bind
INPUT[inlineSelect(class(multiselectmin1), defaultValue(🟥️), option(🟥️), option(🟧️), option(🟨️), option(🟩️)):status]
>>```
>>>
>
>>[!hint]+ E aí?
>>🧠️/📝️/🌲️
>>
>>| ପ꒰ ˶• ༝ •˶꒱ଓ 🍃 `INPUT[toggle:dg-publish]`
>>
>>```meta-bind
INPUT[multiSelect(class(multiselecttemas),option(Conservação-Restauração, 🏺 CR 🏺), option(Programação, 👨🏻‍💻 PC 👨🏻‍💻), option(Divulgação Cientifica, ⚗️ DC ⚗️), option(Comunicação, 🦜 Social 🦜), option(Neurodivergência, 🌈 PCD 🌈), option(Pessoal, 🦝 Eu 🦝)):tema]
>>```
>>>
>>```meta-bind
INPUT[list(class(multiselecttemas)):keywords]
>>```
***

# Configurações Highlighter para vicious

<small>2024-01-07 | 2024-02-16T00:00:00.000-03:00</small>

### Cores do tema

```
--C001: #f18196;
	--C001-RGB: 241, 129, 150;
	--C002: #f19a81;
	--C002-RGB: 241, 154, 129;
	--C003: #ebcb8b;
	--C003-RGB: 241, 201, 129;
	--C004: #e3eb8b;
	--C004-RGB: 227, 235, 139;
	--C005: #bcf181;
	--C005-RGB: 188, 241, 129;
	--C006: #8df181;
	--C006-RGB: 141, 241, 129;
	--C007: #81f1a4;
	--C007-RGB: 129, 241, 164;
	--C008: #8be3eb;
	--C008-RGB: 139, 227, 235;
	--C009: #ab8beb;
	--C009-RGB: 171, 139, 235;
	--C010: #ee81f1;
	--C010-RGB: 238, 129, 241;
	--C011: #f181c5;
	--C011-RGB: 241, 129, 197;
```

### Código a usar

[[Pasted image 20240107123849.png|Open: Pasted image 20240107123849.png]]
![Pasted image 20240107123849.png](/img/user/XX.%20Anexos/Pasted%20image%2020240107123849.png)

***
Referências internas:
- [[2024-01-07   -  📜️ Zotero Research Paper Workflow  Full Comprehensive Setup Guide 🛠️\|2024-01-07   -  📜️ Zotero Research Paper Workflow  Full Comprehensive Setup Guide 🛠️]]

Referências ABNT:


{ .block-language-dataview}
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

| File                                                                                                                                                                                       | Autor                           | Tema                                      | Tags                          | Palavras-Chave                                               |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------- | ----------------------------------------- | ----------------------------- | ------------------------------------------------------------ |
| [[03. Acervos/🐦️/2024-01-14 - barracuda TrAiÇoEiRa (2024-01-14)\|2024-01-14 - barracuda TrAiÇoEiRa (2024-01-14)]]                                                                      | \-barracuda TrAiÇoEiRa          | <ul><li>Pessoal</li></ul>                 | 📥️/🐦️/🟩️                   | <ul><li>arte digital</li></ul>                               |
| [[03. Acervos/🐦️/! 2023-04-13  -  🐦️ Autistic Rose (Rose Matthews) (2023-04-13 )\|! 2023-04-13  -  🐦️ Autistic Rose (Rose Matthews) (2023-04-13 )]]                                  | \-Autistic Rose (Rose Matthews) | <ul><li>Neurodivergência</li></ul>        | <ul><li>📥️/🐦️/🟩️</li></ul> | <ul><li>autismo</li><li>academia</li></ul>                   |
| [[03. Acervos/🎥️/Zotero Research Paper Workflow\|Zotero Research Paper Workflow]]                                                                                                      | \-                              | <ul><li>Programação</li></ul>             | <ul><li>📥️/🎥️/🟩️</li></ul> | <ul><li>zotero</li><li>meuSetup</li><li>obsidian</li></ul>   |
| [[03. Acervos/🎥️/2023-02-21   -  🎥️ Obsidian Dataview Plugin Tutorial 101\|2023-02-21   -  🎥️ Obsidian Dataview Plugin Tutorial 101]]                                                | Bryan Jenks\-                   | <ul><li>Programação</li></ul>             | <ul><li>📥️/🎥️/🟩️</li></ul> | <ul><li>dataview</li><li>obsidian</li><li>tutorial</li></ul> |
| [[03. Acervos/🌐/2024-01-10 - Saiba como referenciar\|2024-01-10 - Saiba como referenciar]]                                                                                             | \-                              | <ul><li>Conservação-Restauração</li></ul> | <ul><li>📥️/🌐/🟩️</li></ul>  | <ul><li>ABNT</li></ul>                                       |
| [[02. Será que interessa/Nota 2024-01-17 \|Nota 2024-01-17 ]]                                                                                                                           | \-                              | <ul><li>Divulgação Cientifica</li></ul>   | <ul><li>📥️/📋/🟥️</li></ul>  | <ul><li>golpe de 64</li><li>material didático</li></ul>      |
| [[02. Será que interessa/NEURODIVERSITY SOME BASIC TERMS & DEFINITIONS • NEUROQUEER\|NEURODIVERSITY SOME BASIC TERMS & DEFINITIONS • NEUROQUEER]]                                       | \-                              | <ul><li>Neurodivergência</li></ul>        | <ul><li>📥️/📰️/🟥️</li></ul> | <ul><li>neurodiversidade</li></ul>                           |
| [[02. Será que interessa/Instructors are learners too Making faculty development accessible to faculty\|Instructors are learners too Making faculty development accessible to faculty]] | \-Sarah Silverman               | <ul><li>Neurodivergência</li></ul>        | <ul><li>📥️/📰️/🟥️</li></ul> | <ul><li>neurodiversidade</li></ul>                           |
| [[02. Será que interessa/Basic OCR in Obsidian\|Basic OCR in Obsidian]]                                                                                                                 | \-                              | <ul><li>Programação</li></ul>             | <ul><li>📥️/📰️/🟥️</li></ul> | <ul><li>obsidian</li><li>meuSetup</li></ul>                  |

{ .block-language-dataview}

***
