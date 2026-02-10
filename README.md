# Proyecto 03: CI/CD con Kubernetes (Kind) y GitHub Actions

Este proyecto implementa un flujo de trabajo completo de **DevOps** para desplegar una aplicación web basada en **Flask** dentro de un clúster de Kubernetes local utilizando **Kind**, orquestado automáticamente mediante **GitHub Actions**.

## 📐 Diseño y Flujo de Trabajo

El sistema está diseñado para automatizar la entrega de software desde el código hasta el despliegue, asegurando consistencia y rapidez.

1.  **Código Fuente**: La aplicación está escrita en Python usando el framework Flask.
2.  **Containerización**: Se utiliza Docker para empaquetar la aplicación y sus dependencias (definidas en `requirements.txt`).
3.  **Orquestación**: Kubernetes gestiona el ciclo de vida de los contenedores, asegurando disponibilidad y escalabilidad.
4.  **Automatización (CI/CD)**:
    *   **Build**: Al hacer push al repositorio, GitHub Actions construye la imagen Docker.
    *   **Push**: La imagen se sube a un registro de contenedores.
    *   **Deploy**: Se aplican los manifiestos en el clúster Kind para actualizar la aplicación.

## 📂 Estructura del Proyecto

La organización de los archivos sigue las mejores prácticas para separar código, infraestructura y configuración:

```text
.
├── .github/workflows/   # Archivos YAML para la configuración del pipeline de CI/CD
├── k8s/                 # Manifiestos de Kubernetes (Deployment, Service, Ingress)
├── app.py               # Código fuente de la aplicación Flask
├── Dockerfile           # Definición de la imagen del contenedor
├── requirements.txt     # Lista de dependencias de Python (Flask)
└── README.md            # Documentación del proyecto
```

## ✅ Lo que se realizó

Durante este proyecto se llevaron a cabo las siguientes tareas clave:

*   **Desarrollo de Microservicio**: Creación de una API ligera con Flask.
*   **Infraestructura como Código**: Definición de recursos de Kubernetes para el despliegue.
*   **Entorno Local**: Configuración de un clúster Kind para simular producción en local.
*   **Pipeline de Integración Continua**: Configuración de GitHub Actions para automatizar pruebas y construcción.

## ⚙️ Proceso de Ejecución Local

Si deseas ejecutar este proyecto manualmente:

1.  **Instalar Dependencias**:
    ```bash
    pip install -r requirements.txt
    ```

2.  **Ejecutar la Aplicación**:
    ```bash
    python app.py
    ```

3.  **Despliegue en Kubernetes (Kind)**:
    ```bash
    # Crear el clúster
    kind create cluster --name project03
    # Aplicar configuración
    kubectl apply -f k8s/
    ```