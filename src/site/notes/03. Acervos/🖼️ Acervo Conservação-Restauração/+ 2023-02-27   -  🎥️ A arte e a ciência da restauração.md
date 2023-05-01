```dataview
table created AS "Criado em", updated as Modificado, tema as Tema, type AS Tipo, canal AS Canal
where titulo != "A arte e a ciência da restauração"
where contains(canal, "CHCnaTV") OR contains(tema, =this.tema)
```