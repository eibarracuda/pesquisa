```dataview
table created AS "Criado em", updated as Modificado, tema as Tema, type AS Tipo, canal AS Canal
where titulo != "Arte Faz Parte - Restauro e conservação de obras de artes"
where contains(canal, "TVUNIMEP") OR contains(tema, =this.tema)
```