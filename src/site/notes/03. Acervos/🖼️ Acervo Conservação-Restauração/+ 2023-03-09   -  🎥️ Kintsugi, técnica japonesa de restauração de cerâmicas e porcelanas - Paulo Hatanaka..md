```dataview
table created AS "Criado em", updated as Modificado, tema as Tema, type AS Tipo, canal AS Canal
where titulo != "Kintsugi, técnica japonesa de restauração de cerâmicas e porcelanas - Paulo Hatanaka."
where contains(canal, "Arte é Investimento") OR contains((tema, this.tema))
```