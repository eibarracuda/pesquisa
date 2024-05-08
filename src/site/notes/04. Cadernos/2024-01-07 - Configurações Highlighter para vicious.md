---
{"dg-publish":true,"permalink":"/04-cadernos/2024-01-07-configuracoes-highlighter-para-vicious/","tags":["🧠️/📝️/🌲️"],"created":"2024-05-08T13:44:45.761-03:00","updated":"2024-02-16T13:07:28.312-03:00"}
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

| File                                                                                                                                                                                                                                               | Autor                 | Tema                          | Tags                          | Palavras-Chave                                               |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------- | ----------------------------- | ----------------------------- | ------------------------------------------------------------ |
| [[02. Feed/2024-01-14 - How to Manage Tasks in Obsidian\|2024-01-14 - How to Manage Tasks in Obsidian]]                                                                                                                                         | \-Tim Miller          | <ul><li>Programação</li></ul> | <ul><li>📥️/📰️/🟥️</li></ul> | <ul><li>obsidian</li><li>meuSetup</li><li>dataview</li></ul> |
| [[02. Feed/2024-01-14 - Import social media accounts into Obsidian Plugin\|2024-01-14 - Import social media accounts into Obsidian Plugin]]                                                                                                     | \-                    | <ul><li>Programação</li></ul> | <ul><li>📥️/📰️/🟥️</li></ul> | <ul><li>obsidian</li><li>meuSetup</li><li>Difusão</li></ul>  |
| [[02. Feed/2024-01-14 - Obsidian for Documenting Memories\|2024-01-14 - Obsidian for Documenting Memories]]                                                                                                                                     | \-adityavikram surana | <ul><li>Programação</li></ul> | <ul><li>📥️/📰️/🟥️</li></ul> | <ul><li>meuSetup</li><li>obsidian</li><li>Galeria</li></ul>  |
| [[02. Feed/2024-01-14 - Promnesia\|2024-01-14 - Promnesia]]                                                                                                                                                                                     | \-                    | <ul><li>Programação</li></ul> | <ul><li>📥️/📰️/🟥️</li></ul> | <ul><li>meuSetup</li><li>Web</li></ul>                       |
| [[02. Feed/2024-01-15   -  How I Set Up My AI-Powered Second Brain in Obsidian (ChatGPT, Search, Assistant, Plugins, Tools)\|2024-01-15   -  How I Set Up My AI-Powered Second Brain in Obsidian (ChatGPT, Search, Assistant, Plugins, Tools)]] | John Mavrick\-        | <ul><li>Programação</li></ul> | <ul><li>📥️/🎥️/🟥️</li></ul> | <ul><li>meuSetup</li><li>obsidian</li></ul>                  |
| [[02. Feed/2024-01-15 - An AI copilot for your second brain\|2024-01-15 - An AI copilot for your second brain]]                                                                                                                                 | \-khoj-ai             | <ul><li>Programação</li></ul> | <ul><li>📥️/📰️/🟥️</li></ul> | <ul><li>obsidian</li><li>meuSetup</li></ul>                  |
| [[02. Feed/2024-01-15 - Easy Exports to Academic Templates\|2024-01-15 - Easy Exports to Academic Templates]]                                                                                                                                   | \-Soft-Material3294   | <ul><li>Programação</li></ul> | <ul><li>📥️/📰️/🟥️</li></ul> | <ul><li>meuSetup</li></ul>                                   |
| [[02. Feed/2024-01-15 - HelpMate for Obsidian\|2024-01-15 - HelpMate for Obsidian]]                                                                                                                                                             | \-TfTHacker           | <ul><li>Programação</li></ul> | <ul><li>📥️/📰️/🟥️</li></ul> | <ul><li>meuSetup</li><li>obsidian</li></ul>                  |
| [[02. Feed/2024-01-16 - Compile many Obsidian notes down to one\|2024-01-16 - Compile many Obsidian notes down to one]]                                                                                                                         | \-mgmeyers            | <ul><li>Programação</li></ul> | <ul><li>📥️/📰️/🟥️</li></ul> | <ul><li>obsidian</li><li>meuSetup</li></ul>                  |

{ .block-language-dataview}

***
