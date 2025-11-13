# Práctica de Codelabs de Android - Jetpack Compose

Este repositorio es la entrega de la práctica de clase, donde se recopila el código fuente (`src`) de los Codelabs de Android completados. El objetivo principal es familiarizarse con el desarrollo de UI moderno en Android utilizando **Kotlin** y **Jetpack Compose**.

---

## Estructura del Repositorio

El repositorio está organizado en carpetas, donde cada carpeta representa un proyecto de Codelab individual. Dentro de cada una de estas carpetas se encuentra el directorio `src` que contiene todo el código fuente de Kotlin y los recursos de dicho proyecto.

---

## Proyectos Incluidos

### **FirstAndroidApp**  
**Codelab:** Crea tu primera app de Android  
**Descripción:** Introducción básica a un proyecto de Compose, modificando un componente `Text` y `Surface`.

---

### **BasicsCodelab**  
**Codelab:** Conceptos básicos de Jetpack Compose  
**Descripción:** App más completa que enseña el manejo de estado (`remember`), creación de listas (`LazyColumn`), una pantalla de *onboarding* y cómo expandir/contraer elementos con animación.

---

### **BasicLayouts**  
**Codelab:** Diseños básicos en Jetpack Compose  
**Descripción:** Creación de una app de bienestar (“Soothe”) desde cero, enfocándose en estructuras de diseño complejas como `SearchBar`, `LazyRow`, `LazyHorizontalGrid`, `Scaffold` y `NavigationBar`.

---

## Aspectos Interesantes del Ejercicio

Durante la realización de estos Codelabs surgieron varios conceptos clave del desarrollo moderno en Android que considero fundamentales:

### 1. El Paradigma Declarativo de Compose

Lo más interesante es el cambio de mentalidad frente al antiguo sistema de Vistas (XML). Con Compose, no “modificamos” la UI, sino que la *describimos* en función de un estado.  
Cuando el estado cambia (`remember { mutableStateOf(...) }`), Compose “recompone” la UI automáticamente.  
Esto se vio claramente en el Codelab *BasicsCodelab* al expandir una tarjeta.

---

### 2. Composición de Layouts

El Codelab *BasicLayouts* (la app “Soothe”) fue excelente para entender cómo anidar componentes.  
La potencia de Compose radica en crear componentes pequeños y reutilizables (`AlignYourBodyElement`, `FavoriteCollectionCard`) y luego combinarlos en estructuras más grandes como `LazyRow` (scroll horizontal) y `LazyVerticalGrid` (cuadrícula de favoritos).

---

### 3. La Importancia del Archivo `build.gradle.kts`

Un proyecto no funciona solo con el código Kotlin. Fue crucial entender el sistema de dependencias de Gradle:

- **Gestión de dependencias:**  
  Para usar componentes adicionales, como iconos (`Icons.Filled.ExpandMore`, `Icons.Default.Search`), fue necesario añadir explícitamente la librería  
  `androidx.compose.material:material-icons-extended` en el `build.gradle.kts` del módulo App.
  
- **Sincronización:**  
  Cualquier cambio requiere un **Sync Now** para descargar y reconocer las nuevas bibliotecas.

---

### 4. Sistema de Theming (`Theme.kt`)

Al compilar el proyecto *BasicLayouts*, aparecieron múltiples errores de `Unresolved reference` relacionados con `BasicLayoutsTheme`.  
Aprendí que cada proyecto de Compose genera su propio sistema de temas (`ui/theme/Theme.kt`), donde se definen:

- `colorScheme`  
- `typography`

Para evitar errores, todas las funciones `@Composable` y `@Preview` deben envolverse en el tema específico del proyecto  
(ejemplo: `BasicLayoutsCodeLabTheme { ... }`).

---
