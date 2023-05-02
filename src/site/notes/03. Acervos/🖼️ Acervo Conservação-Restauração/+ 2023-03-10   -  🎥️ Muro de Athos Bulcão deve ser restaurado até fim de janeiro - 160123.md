```dataview
table created AS "Criado em", updated AS "Modificado", tema AS "Tema", type AS "Tipo", canal AS "Canal"
where titulo != "Muro de Athos Bulcão deve ser restaurado até fim de janeiro - 16/01/23"
where contains(canal, "Câmara dos Deputados") OR contains((tema, this.tema))
```