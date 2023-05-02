```dataview
table created AS "Criado em", updated AS "Modificado", tema AS "Tema", type AS "Tipo", canal AS "Canal"
where titulo != "Restaurarando Uma PINTURA de Gesso!!"
where contains(canal, "Iolane Caron") OR contains((tema, this.tema))
```