```dataview
table created AS "Criado em", updated as Modificado, tema as Tema, type AS Tipo, canal AS Canal
where titulo != "Restauração de Santo Antonio"
where contains(canal, "Deum Laudamus Arte Sacra e Restauração") OR contains(tema, =this.tema)
```