# Política MABE · CI económico y seguro

Esta política aplica a todo desarrollo conectado a Railway.

1. Trabajar en una rama y **agrupar cambios relacionados** antes de consumir CI.
2. Abrir el pull request como **Draft** mientras continúe la iteración. Los runners pesados deben ejecutarse cuando el lote esté listo para revisión.
3. Antes de marcar **Ready for review**, ejecutar las validaciones locales disponibles y corregir errores obvios.
4. Mantener `concurrency` con `cancel-in-progress: true` para cancelar ejecuciones obsoletas de la misma rama/PR.
5. Evitar repetir en `main` una suite que ya validó el mismo cambio en el PR, cuando el flujo de merge permita identificarlo de forma segura.
6. Preferir Linux y runners de menor costo **solo cuando la suite probada no se vuelva más lenta ni menos estable**.
7. Builds caros (Windows, imágenes, instaladores, suites profundas) deben ser manuales, programados o ejecutarse una sola vez al integrar a `main`, salvo que exista una razón técnica documentada.
8. Cambios únicamente en `.github/**` no deben provocar un redeploy en Railway.
9. No duplicar build/deploy en GitHub Actions cuando Railway ya realiza esa función.
10. Fusionar preferentemente con **squash merge** para que un lote de trabajo produzca un solo cambio en la rama de despliegue.

Objetivo: conservar controles de calidad y trazabilidad con el menor número razonable de minutos de runner y despliegues.
