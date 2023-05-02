```dataview
table created AS "Criado em", updated AS "Modificado", tema AS "Tema", type AS "Tipo", canal AS "Canal"
where titulo != "Restaurado Muro Escultórico de Athos Bulcão - 31/01/23"
where contains(canal, "Câmara dos Deputados") OR contains((tema, this.tema))
```