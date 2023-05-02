```dataview
table created AS "Criado em", updated AS "Modificado", tema AS "Tema", type AS "Tipo", canal AS "Canal"
where titulo != "Muro Escultórico passa por restauração e higienização - Obra de Athos Bulcão - 26/01/23"
where contains(canal, "Câmara dos Deputados") OR contains((tema, this.tema))
```