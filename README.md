# Prueba Técnica – Fullstack Developer

## 📌 Descripción General

El objetivo de esta prueba es evaluar tu capacidad para diseñar e implementar una aplicación **Fullstack**, integrando:

- **Frontend:** React  
- **Backend:** Arquitectura en AWS (a elección del candidato)  
- **Infraestructura como código:** AWS CDK **o** Terraform  

La aplicación debe permitir que usuarios **anónimos** creen solicitudes mediante un formulario, mientras que un **usuario autenticado (admin)** podrá visualizar todas las solicitudes.

---

## 1. Requerimiento Funcional

### 1.1 Usuario Anónimo
- Accede sin autenticación.
- Puede completar un **formulario simple** para crear una solicitud.
- Al enviar:
  - Los datos se envían al backend mediante un endpoint público.
  - La solicitud se almacena en la base de datos.
  - Se muestra un mensaje de confirmación.

### 1.2 Usuario Autenticado (Admin único)
- Accede a una ruta separada (ej.: `/admin`).
- Debe autenticarse usando el mecanismo que prefieras:
  - Cognito  
  - JWT  
  - Basic Auth  
  - Otro método simple y funcional  
- Visualiza **todas las solicitudes** mediante una tabla.

> No se requiere edición o eliminación de solicitudes. Solo lectura.

---

## 2. Funcionalidades Requeridas

### 2.1 Frontend (React)

Debe incluir:

- **Formulario público** para crear solicitudes.
- **Pantalla de login** para el admin.
- **Pantalla de administración** para listar solicitudes.

Requisitos mínimos:
- React (idealmente TypeScript)
- Hooks para manejo de estado
- Llamadas al backend vía fetch/axios
- Diseño responsivo simple
- Código modular y legible

---

### 2.2 Backend (Tecnología a elección)

Puedes elegir **una** arquitectura en AWS:

#### **A) Serverless**
- AWS Lambda  
- API Gateway  
- (Opcional) Lambda con Docker  

#### **B) ECS (Fargate)**
- Contenedor Docker
- Servicio ECS
- ALB o API Gateway

#### **C) EKS**
- Pod/Deployment
- Ingress Controller / ALB
- Helm (opcional)

Debes incluir una **breve justificación** de tu elección tecnológica.

---

### Endpoints requeridos

#### `POST /solicitudes`
- Público  
- Recibe los datos del formulario  
- Guardar la solicitud  

#### `GET /solicitudes`
- Protegido (solo admin)  
- Retorna todas las solicitudes  

---

### Persistencia (a elección)
- DynamoDB  
- Aurora Serverless v2  
- RDS  
- Otra base administrada (con justificación)

**Modelo sugerido:**
```json
{
  "id": "string",
  "nombre": "string",
  "email": "string",
  "monto": 0,
  "tipo": "string",
  "comentarios": "string",
  "fechaCreacion": "string"
}

```

## 3. Infraestructura (IaC)

Debes declarar la infraestructura con:

- AWS CDK (TypeScript o Python)
o

- Terraform

### Recursos esperados (según arquitectura elegida):

- API Gateway o ALB

- Lambda / ECS Service / EKS Deployment

- Base de datos

- Roles IAM

- VPC (opcional, valorado)

- S3 + Cloudfront (Frontend)


## 4. Entregables

Tu entrega debe incluir:

### 1. Frontend

- Código React

- README con instrucciones para correr local

### 2. Backend

- Código fuente (Python / Javascript/ Typescript) (Priorizar lenguaje de mayor dominio del candidato)

- Dockerfile (si aplica)

- Instrucciones para probar/deploy

### 3. Infraestructura

- CDK o Terraform

- Pasos claros para desplegar

- Variables necesarias

## 4. Documentación

- Justificación de arquitectura elegida

- Diagrama simple de arquitectura (Draw.io u otro similar)

- Explicación del flujo general

### 5. Opcional (suma puntos)

- Tests (frontend o backend)

- CI/CD simple

- Despliegue en AWS personal

- Colección Postman/Insomnia


## 5. Criterios de Evaluación
### Frontend

- Estructura del código

- Manejo correcto del formulario

- Integración limpia con backend

- Buenas prácticas de React

### Backend

- Diseño y modularidad del código

- Validaciones y manejo de errores

- Seguridad del endpoint protegido

- Implementación coherente

### Infraestructura

- Uso adecuado de IaC

- Modularidad

- Correcta definición de permisos

- Claridad del despliegue

### Calidad Global

- Documentación

- Organización

- Claridad del repositorio

- Simplicidad y legibilidad

## 6. Instrucciones Finales

Mantén la solución simple y funcional.

Puedes usar librerías según tu criterio.

Si no puedes desplegar alguna parte, explica cómo lo harías.

Esta prueba busca evaluar tu manejo fullstack del ecosistema AWS + React.