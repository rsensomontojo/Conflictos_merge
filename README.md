# Flujo Básico para Colaborar en un Repositorio Git

Este documento describe el flujo básico para que dos personas trabajen en el mismo repositorio Git, incluye cómo manejar conflictos cuando ambos editan los mismos archivos.

---

## Flujo de Trabajo para la primera persona

1. **Inicializar o clonar el repositorio**:
   - Si es un nuevo repositorio, inicia uno con:
     ```bash
     git init
     ```
   - Si ya existe un repositorio remoto, clónalo con:
     ```bash
     git clone <url-del-repositorio-remoto>
     ```

2. **Realizar cambios y hacer commit**:
   - Edita los archivos en tu máquina.
   - Guarda los cambios en los archivos de tu máquina
   - Añade los cambios al área de preparación con:
     ```bash
     git add <archivo-o-directorio>
     ```
   - Realiza un commit con:
     ```bash
     git commit -m "Explicación breve del commit"
     ```

3. **Enlazar el repositorio local con el remoto**:
   - Si es la primera vez, enlaza tu repositorio local con el remoto:
     ```bash
     git remote add origin <url-del-repositorio-remoto>
     ```

4. **Subir cambios al repositorio remoto**:
   - Sube los cambios a la rama principal (por ejemplo, `main`):
     ```bash
     git push origin main
     ```

---

## Flujo de Trabajo para la segunda persona

1. **Clonar el repositorio**:
   - Clona el repositorio remoto en tu máquina:
     ```bash
     git clone <url-del-repositorio-remoto>
     ```

2. **Obtener cambios recientes**:
   - Antes de nada, obtén los últimos cambios del repositorio remoto:
     ```bash
     git pull origin main
     ```
     
3. **Realizar cambios y hacer commit**:
   - Edita los archivos en tu máquina.
   - Guarda los archivos en tu máquina con los cambios
   - Añade los cambios al área de preparación con:
     ```bash
     git add <archivo-o-directorio>
     ```
   - Realiza un commit con:
     ```bash
     git commit -m "Mensaje descriptivo del commit"
     ```
   -Modifica el archivo:
      ```bash
     git merge origin main/carpeta/rama
     ```
   

---

## Manejo de Conflictos al Hacer Merge

Cuando dos personas trabajan en el mismo archivo o directorio (lo normal es la división de áreas de trabajo para que no haya conflicto) , es posible que surjan conflictos al intentar fusionar (`merge`) los cambios. Git intentará fusionar automáticamente, pero si los cambios son incompatibles (por ejemplo, ambas personas editaron la misma línea de un archivo), se producirá un **conflicto de merge**.

### ¿Qué sucede durante un conflicto de merge?

1. **Git marca los archivos en conflicto**:
   - Cuando ejecutas `git pull` o `git merge`, Git te notificará que hay conflictos.
   - Los archivos en conflicto contendrán marcas especiales que indican las diferencias:
     ```plaintext
     <<<<<<< HEAD
     Cambios de Persona 1
     =======
     Cambios de Persona 2
     >>>>>>> branch-name
     ```
   - `<<<<<<< HEAD` indica los cambios de la rama actual (Persona 1).
   - `=======` separa los cambios de la rama actual y los cambios de la rama que estás fusionando (Persona 2).
   - `>>>>>>> branch-name` indica los cambios de la rama que estás fusionando.

2. **Resolución manual del conflicto**:
   - Abre el archivo en conflicto en tu editor de texto.
   - Decide qué cambios conservar:
     - Puedes mantener los cambios de una de las personas.
     - O fusionar ambos cambios manualmente.
   - Elimina las marcas `<<<<<<<`, `=======` y `>>>>>>>` una vez que hayas resuelto el conflicto.

3. **Añadir los archivos resueltos**:
   - Después de resolver el conflicto, añade los archivos al área de preparación:
     ```bash
     git add <archivo>
     ```

4. **Finalizar el merge**:
   - Una vez que todos los conflictos estén resueltos y los archivos añadidos, finaliza el merge con un commit:
     ```bash
     git commit -m "Resuelto conflicto de merge entre Persona 1 y Persona 2"
     ```

5. **Subir los cambios al repositorio remoto**:
   - Finalmente, sube los cambios fusionados al repositorio remoto:
     ```bash
     git push origin main
     ```

---

## Consejos para Evitar Conflictos

1. **Comunicación constante**:
   - La coordinación es fundamental para evitar trabajar en los mismos archivos al mismo tiempo.

2. **Trabajar en ramas separadas**:
   - Crea ramas (`branches`) para trabajar en funcionalidades específicas. Luego, fusiona (`merge`) las ramas cuando estén listas.

3. **Hacer `git pull` frecuentemente**:
   - Antes de empezar a trabajar, siempre obtén los últimos cambios del repositorio remoto con:
     ```bash
     git pull origin main
     ```


---
