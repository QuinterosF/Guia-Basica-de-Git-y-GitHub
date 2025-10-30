# Guía rápida de Git y GitHub
## UNSXX

![Image](image.png)

## Inicialización y configuración básica

```bash
git init
```

* Inicia un nuevo repositorio Git en el directorio actual. (Crea la carpeta `.git` que almacenará todo el historial del proyecto).

```bash
git config --global user.name "TuNombre"
git config --global user.email "tuemail@example.com"
```

* Configura tu nombre y correo globalmente (se usarán en todos tus commits).
Puedes usar `--local` en lugar de `--global` para configurarlo solo en un proyecto.

---

## 📂 Control de versiones local

```bash
git status
```

* Muestra el estado actual de los archivos (qué está modificado, qué está en staging y qué falta agregar).

```bash
git add <archivo>
git add .
```

* Agrega archivos al **staging area** (zona de preparación).
`git add .` agrega **todos los archivos modificados** del directorio actual.

```bash
git commit -m "mensaje"
```

* Crea un **commit** (punto de control) con los archivos que están en el staging area.
Es recomendable usar mensajes cortos y descriptivos como “Agrega función de login”.

```bash
git log
```

* Muestra el historial de commits (ID, autor, fecha y mensaje).

```bash
git diff <archivo>
```

* Muestra los cambios hechos en un archivo antes de hacer `add` o `commit`.

```bash
git checkout -- <archivo>
```

* Revierte los cambios del archivo al último commit guardado (descarta cambios sin guardar).

---

## 🌿 Trabajo con ramas

```bash
git branch
```

* Muestra la lista de ramas del proyecto y cuál está activa.

```bash
git branch <nombre_rama>
```

* Crea una nueva rama a partir de la actual.

```bash
git checkout <nombre_rama>
```

* Cambia a la rama indicada.

```bash
git merge <nombre_rama>
```

* Une la rama indicada con la actual (mezcla los cambios de ambas).

---

## ☁️ Repositorios remotos (GitHub)

```bash
git remote add origin https://github.com/QuinterosF/my-project.git
```

* Conecta tu repositorio local con el remoto en GitHub.

```bash
git remote -v
```

* Muestra los repositorios remotos configurados (origen y destino de fetch/push).

```bash
git push origin main
```

* Sube tus commits locales a la rama `main` del repositorio remoto.

```bash
git pull origin main
```

* Descarga e integra los cambios que hay en la rama `main` del repositorio remoto.
(Se usa cuando hay varios desarrolladores o trabajás desde varios equipos).

```bash
git clone https://github.com/Usuario/Repo.git
```

* Crea una copia local de un repositorio remoto.

---

## 🔁 Pull Requests y Forks (colaboración)

1. **Fork:** Crea una copia de un repositorio ajeno en tu cuenta.
2. **Clona tu fork:**

   ```bash
   git clone https://github.com/TuUsuario/RepoFork.git
   ```
3. Crea una rama para tus cambios:

   ```bash
   git checkout -b contribucion
   ```
4. Realizá cambios, haz `git add` y `git commit`.
5. Subí tu rama:

   ```bash
   git push origin contribucion
   ```
6. En GitHub, hacé clic en **Compare & pull request** → enviá el PR al repo original.
7. Desde la cuenta del propietario, hacé clic en **Merge pull request** → **Confirm merge**.

---

## 🔐 Autenticación (nuevo sistema con tokens)

GitHub ya **no acepta contraseñas** al usar HTTPS, solo **tokens personales (PAT)**.

```bash
git remote set-url origin https://<usuario>:<TOKEN>@github.com/<usuario>/<repo>.git
```

Ejemplo:

```bash
git remote set-url origin https://Quinteros-dev:ghp_ABC123TOKENxyz@github.com/Quinteros-dev/my-project.git
```

👉 Esto actualiza la conexión remota con tu token para que puedas hacer `push` sin errores de permiso.

---

## 🧰 Comandos útiles extra

```bash
git fetch
```

* Descarga información de ramas remotas sin fusionarla aún (ideal para revisar antes de un pull).

```bash
git reset --hard HEAD
```

* Revierte el proyecto al último commit, eliminando todos los cambios no guardados (⚠️ cuidado).

```bash
git stash
```

* Guarda temporalmente los cambios sin hacer commit (por si querés cambiar de rama sin perderlos).

```bash
git restore <archivo>
```

* Versión moderna de `checkout -- <archivo>` (recomendado desde Git 2.23+).

---

## 🧭 Flujo general de trabajo

1. `git init`
2. `git add .`
3. `git commit -m "Primer commit"`
4. `git branch -M main` (para renombrar la rama principal si aún se llama master)
5. `git remote add origin https://github.com/usuario/repo.git`
6. `git push -u origin main`
7. (Luego, solo usar `git add`, `git commit`, `git push` según los cambios)
