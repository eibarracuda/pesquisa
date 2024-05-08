---
{"dg-publish":true,"permalink":"/04-cadernos/2024-01-14-referencia-abnt-integracao-zotero-obsidian/","tags":["🧠️/📝️/🌿️"],"created":"2024-05-08T13:44:45.767-03:00","updated":"2024-02-16T12:24:16.184-03:00"}
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
>>🧠️/📝️/🌿️
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

# Referência ABNT - integração zotero obsidian

## Importações do Zotero

Com a assistência dos vídeos do [[03. Acervos/☎️/Bryan Jenks\|Bryan Jenks]], porém adaptados para ABNT:

```
{% for annotation in annotations -%}
	{%if annotation.annotatedText  -%}
		- <mark class="hltr-{{annotation.colorCategory | lower}}">"{{annotation.annotatedText}}" ({% for creator in creators -%}
{%if creator.lastName -%}
		{{creator.lastName | upper}} {%endif %}{% endfor -%}	, {{date | format("YYYY")}}, p. {{annotation.page}}.)</mark></br>
	{%endif %}
	{%if annotation.imageRelativePath -%}
	![[{{annotation.imageRelativePath}}]]
	{%endif %}
{% if annotation.comment %}
	- {{annotation.comment}}</br>
{% endif %}
{% endfor -%}
```
