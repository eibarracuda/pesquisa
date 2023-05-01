```dataview
table created AS "Criado em", updated as Modificado, tema as Tema, type AS Tipo, canal AS Canal
where titulo != "Restauração Arte Sacra TCC Templo da Arte"
where contains(canal, "Titina Corso") OR contains(tema, =this.tema)
```