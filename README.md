# Laboratorio público DevSecOps

> **Aplicación sintética y educativa.** No contiene código, datos, secretos ni
> infraestructura de SaleADS. Su propósito es validar PR → CI → build único →
> Trivy pre-publish mediante reusable workflows fijados por SHA.

# DevSecOps PoC — Spring Boot

Microservicio privado y desechable para validar controles CI/CD sobre Java 21/Spring Boot sin tocar entornos corporativos.

## Aviso de seguridad

Este repositorio pertenece a un laboratorio DevSecOps aislado. Está diseñado para incorporar vulnerabilidades intencionales y controladas en la tarea de escenarios del PoC.

- No desplegar en producción.
- No conectar a datos, identidades, secretos, redes ni registros corporativos.
- No hacerlo público mientras existan escenarios vulnerables.
- Eliminar repositorios, artifacts y recursos temporales al finalizar el PoC.

## Requisitos

- Java 21
- Maven Wrapper incluido
- Docker opcional

## Ejecución local

~~~bash
./mvnw spring-boot:run
curl http://localhost:8080/actuator/health
~~~

## Pruebas

~~~bash
./mvnw test
~~~

## Política CI

GitHub Actions reporta toda la deuda y bloquea únicamente findings nuevos. El baseline Trivy versionado está en `.security/.trivyignore`; un cambio no puede aprobar su propio baseline.

## Contenedor

~~~bash
docker build -t devsecops-poc-spring-boot:local .
docker run --rm -p 8080:8080 devsecops-poc-spring-boot:local
~~~

## Ciclo de vida

Repositorio temporal del PoC. Se elimina al completar la evidencia y la decisión go/no-go.
