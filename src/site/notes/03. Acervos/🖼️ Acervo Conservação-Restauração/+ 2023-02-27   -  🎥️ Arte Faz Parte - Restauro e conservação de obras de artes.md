```dataview
table created AS "Criado em", updated AS "Modificado", tema AS "Tema", type AS "Tipo", canal AS "Canal"
where titulo != "Arte Faz Parte - Restauro e conservação de obras de artes"
where contains(canal, "TVUNIMEP") OR contains((tema, this.tema))
```