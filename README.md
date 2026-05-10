# Expo 54 — Template Local

Template base para aplicaciones móviles con **Expo 54** y **React Native 0.81**, con arquitectura modular y un conjunto de herramientas preconfiguradas para acelerar el desarrollo desde cero.

---

## Stack Tecnológico

| Categoría | Tecnología | Versión |
|---|---|---|
| Framework | Expo | 54.x |
| Runtime | React Native | 0.81.x |
| Lenguaje | JavaScript (JSX) | — |
| Navegación | React Navigation | 7.x |
| Estado global | Zustand + AsyncStorage | 5.x |
| Estilos | NativeWind (Tailwind CSS) | 4.x |
| UI Components | React Native Paper | 5.x |
| Iconos | Lucide React Native | 1.x |
| Animaciones | React Native Reanimated | 4.x |
| Builds | EAS Build | — |

---

## Estructura del Proyecto

```
├── index.js                  # Punto de entrada (registerRootComponent)
├── RootLayout.js             # Providers raíz (Theme, Toast)
├── App.js                    # NavigationContainer + SafeAreaProvider
├── app.json                  # Configuración Expo
├── eas.json                  # Configuración EAS Build
├── tailwind.config.js        # Configuración Tailwind / NativeWind
├── global.css                # Directivas base de Tailwind
│
└── src/
    ├── components/
    │   ├── ui/               # Componentes reutilizables (Header, Containers, Forms, Toast…)
    │   ├── modals/           # Modales genéricos (formulario, selector)
    │   └── GENERICO/         # Versiones plantilla de modales
    │
    ├── feature/
    │   └── feature_1/        # Módulo de ejemplo: gestión de clientes
    │       └── store/        # Zustand store con persistencia
    │
    ├── navigation/
    │   ├── RootStack.js      # Navigator principal (Stack)
    │   └── TabNavigator.js   # Navegación por pestañas (Bottom Tabs)
    │
    ├── screens/
    │   ├── TabOneScreen.js
    │   ├── TabTwoScreen.js
    │   ├── DetailsScreen.js
    │   └── setting/
    │       └── ModalConfig.js
    │
    ├── theme/
    │   ├── theme.js          # Paleta de colores (light / dark)
    │   ├── ThemeContext.js   # Context Provider
    │   └── useTheme.js       # Hook de acceso al tema
    │
    └── utils/
        └── formatDato.js     # Formateador de fechas (locale es)
```

---

## Características Incluidas

### Navegación
- **Stack Navigator** como raíz con soporte para pantalla de detalles.
- **Bottom Tab Navigator** con 2 pestañas iniciales, listo para escalar.
- Encabezado (`Header`) integrado con el sistema de temas.

### Sistema de Temas
- Soporte para modo **claro y oscuro** basado en `useColorScheme`.
- Paleta semántica: `primary`, `secondary`, `accent`, `danger`, `success`, `warning`, `info`, entre otros.
- Hook `useTheme()` disponible en cualquier componente.

### Estado Global
- **Zustand** con middleware `persist` para almacenamiento automático en `AsyncStorage`.
- Store de ejemplo (`useClientesStore`) con operaciones CRUD completas.

### Estilos
- **NativeWind 4** habilitado: usa clases de Tailwind directamente en JSX de React Native.
- Alias de importación `@/` apuntando a `src/` para rutas limpias.

### Componentes UI Listos
- `ContainerTabs` — contenedor base para pantallas con tabs.
- `Header` — encabezado con título y botón de perfil.
- `CamposFormulario` — inputs de formulario estilizados.
- `CeroItems` — estado vacío reutilizable.
- `CustomToast` — notificaciones toast personalizadas.
- `SkeletonLoadingInfo` — placeholder de carga con shimmer.
- `ModalFormulario` / `ModalSelector` — modales listos para usar.

### Build & Deploy
- **EAS Build** configurado con tres perfiles:
  - `development` — con dev client habilitado.
  - `preview` — distribución interna.
  - `production` — release para stores.
- **Expo Updates** habilitado con política `appVersion`.

---

## Requisitos

- Node.js 18+
- npm o yarn
- Expo CLI (`npm install -g expo-cli`)
- Para builds nativos: cuenta en [expo.dev](https://expo.dev) y EAS CLI

---

## Instalación

```bash
# Clonar el repositorio
git clone <url-del-repositorio>
cd Expo54-Template-local

# Instalar dependencias
npm install

# Iniciar el servidor de desarrollo
npx expo start
```

### Plataformas

```bash
# Android
npx expo start --android

# iOS
npx expo start --ios

# Web
npx expo start --web
```

---

## Builds con EAS

```bash
# Build de desarrollo (requiere dispositivo físico o emulador)
eas build --profile development --platform android

# Build de preview
eas build --profile preview --platform all

# Build de producción
eas build --profile production --platform all
```

---

## Personalización

1. **Nombre de la app** — editar `app.json` → `name`, `slug` y el package en `android.package`.
2. **Paleta de colores** — modificar `src/theme/theme.js`.
3. **Nuevas features** — crear carpetas en `src/feature/<nombre>/` siguiendo el patrón de `feature_1`.
4. **Nuevas pantallas** — agregar en `src/screens/` y registrar en `src/navigation/RootStack.js` o `TabNavigator.js`.

---

## Convenciones

- Alias `@/` para importar desde `src/` (ej. `import Header from '@/components/ui/Header'`).
- Stores de Zustand en `src/feature/<nombre>/store/`.
- Componentes de UI genéricos en `src/components/ui/`.
