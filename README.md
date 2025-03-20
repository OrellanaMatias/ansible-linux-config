# Configuración de Servidor con Ansible

Este proyecto contiene la configuración automatizada de servidores usando Ansible. Incluye roles para la configuración base del sistema, servidor web Nginx, despliegue de aplicaciones y configuración SSH.

## Requisitos Previos

- Ansible instalado en la máquina de control
- Acceso SSH a los servidores objetivo
- Python instalado en los servidores objetivo

## Estructura del Proyecto

```
.
├── inventory.ini          # Inventario de servidores
├── setup.yml             # Playbook principal
└── roles/                # Roles de Ansible
    ├── base/             # Configuración base del sistema
    ├── nginx/            # Configuración del servidor web
    ├── app/              # Configuración de la aplicación
    └── ssh/              # Configuración SSH
```

## Roles

### Base
Configuraciones básicas del sistema.

### Nginx
Instala y configura el servidor web Nginx con configuraciones de seguridad básicas.

### App
Configura el entorno para la aplicación web.

### SSH
Gestiona la configuración de SSH para mayor seguridad.

## Uso

1. Configure su inventario en `inventory.ini`:
   ```ini
   [servers]
   servidor1 ansible_host=ip_del_servidor
   ```

2. Ejecute el playbook completo:
   ```bash
   ansible-playbook -i inventory.ini setup.yml
   ```

3. Para ejecutar roles específicos, use tags:
   ```bash
   ansible-playbook -i inventory.ini setup.yml --tags "nginx,app"
   ```

## Tags Disponibles

- `base`: Configuración base del sistema
- `nginx`: Configuración del servidor web
- `app`: Configuración de la aplicación
- `ssh`: Configuración SSH

## Personalización

Puede personalizar la configuración modificando las variables en los archivos de configuración de cada rol.

## Seguridad

Este playbook incluye configuraciones básicas de seguridad para Nginx y SSH. Asegúrese de revisar y ajustar estas configuraciones según sus necesidades específicas.