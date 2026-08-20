# KAN-118 — Validación CI de Spring Boot

Esta rama ejecuta el control verde del pipeline DevSecOps baseline/delta.

## Resultado esperado

- Tests y build del stack terminan correctamente.
- Gitleaks no encuentra secretos.
- Semgrep no encuentra regresiones nuevas.
- Trivy filesystem e imagen reportan delta CRITICAL/HIGH igual a cero.
- SARIF y JSON delta quedan conservados como artifacts.

La evidencia válida es la ejecución remota de GitHub Actions asociada al Pull Request.
