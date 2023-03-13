```dataviewjs
dv.paragraph(`> [!${dv.current().Caption ? 'SUCCESS' : 'FAILURE'}] ${dv.current().Caption ? 'Possui legendas' : 'Não possui legendas'}`)
```