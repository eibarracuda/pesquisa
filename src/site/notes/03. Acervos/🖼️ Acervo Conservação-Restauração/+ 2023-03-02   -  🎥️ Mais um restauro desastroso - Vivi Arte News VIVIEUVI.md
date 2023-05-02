```dataview
table created AS "Criado em", updated AS "Modificado", tema AS "Tema", type AS "Tipo", canal AS "Canal"
where titulo != "Mais um restauro desastroso - Vivi Arte News #VIVIEUVI"
where contains(canal, "vivieuvi") OR contains((tema, this.tema))
```