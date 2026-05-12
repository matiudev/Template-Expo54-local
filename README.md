# 📱 Expo 54 — Template Local

> Template base para aplicaciones móviles con **Expo 54** y **React Native 0.81**, con arquitectura modular y herramientas preconfiguradas para acelerar el desarrollo desde cero.

---

## 🛠️ Stack Tecnológico

| Categoría | Tecnología | Versión |
|-----------|-----------|---------|
| Framework | Expo | 54.x |
| Runtime | React Native | 0.81.x |
| Lenguaje | JavaScript (JSX) | — |
| Navegación | React Navigation | 7.x |
| Estado Global | Zustand + AsyncStorage | 5.x |
| Estilos | NativeWind (Tailwind CSS) | 4.x |
| UI Components | React Native Paper | 5.x |
| Íconos | Lucide React Native | 1.x |
| Animaciones | React Native Reanimated | 4.x |
| Builds | EAS Build | — |

---

## ✨ Características Incluidas

### 🧭 Navegación
- **Stack Navigator** como raíz con soporte para pantalla de detalles.
- **Bottom Tab Navigator** con 2 pestañas iniciales, listo para escalar.
- Encabezado (`Header`) integrado con el sistema de temas.

### 🎨 Sistema de Temas
- Soporte para modo **claro y oscuro** basado en `useColorScheme`.
- Paleta semántica: `primary`, `secondary`, `accent`, `danger`, `success`, `warning`, `info`, entre otros.
- Hook `useTheme()` disponible en cualquier componente.

### 🗄️ Estado Global
- **Zustand** con middleware `persist` para almacenamiento automático en `AsyncStorage`.
- Store de ejemplo (`useClientesStore`) con operaciones CRUD completas.

### 🖼️ Componentes UI Listos
- `ContainerTabs` — contenedor base para pantallas con tabs.
- `Header` — encabezado con título y botón de perfil.
- `CamposFormulario` — inputs de formulario estilizados.
- `CeroItems` — estado vacío reutilizable.
- `CustomToast` — notificaciones toast personalizadas.
- `SkeletonLoadingInfo` — placeholder de carga con shimmer.
- `ModalFormulario` / `ModalSelector` — modales listos para usar.

### ⚙️ Estilos y Configuración
- **NativeWind 4** habilitado: usá clases de Tailwind directamente en JSX.
- Alias `@/` apuntando a `src/` para rutas de importación limpias.
- **EAS Build** configurado con tres perfiles: `development`, `preview` y `production`.

---

## 📁 Estructura del Proyecto

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
    │       ├── components/   # Componentes propios del módulo
    │       ├── screens/      # Pantallas del módulo
    │       ├── service/      # Lógica de negocio y llamadas a API/Supabase
    │       ├── store/        # Zustand store con persistencia
    │       └── utils/        # Funciones utilitarias específicas del módulo
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

## 🚀 Instalación y Configuración

### Prerrequisitos
- **Node.js** 18+
- **Expo CLI**: `npm install -g expo-cli`
- Para builds nativos: cuenta en [expo.dev](https://expo.dev) y EAS CLI

### Pasos

```bash
# 1. Clonar el repositorio
git clone <url-del-repositorio>
cd Expo54-Template-local

# 2. Instalar dependencias
npm install

# 3. Iniciar el servidor de desarrollo
npx expo start
```

### Plataformas

```bash
npx expo start --android
npx expo start --ios
npx expo start --web
```

### Builds con EAS

```bash
# Instalar EAS CLI
npm install -g eas-cli

# Development
eas build --profile development --platform android

# Preview
eas build --profile preview --platform all

# Production
eas build --profile production --platform all
```

---

## 🔧 Personalización

1. **Nombre de la app** — editar `app.json` → `name`, `slug` y `android.package`.
2. **Paleta de colores** — modificar `src/theme/theme.js`.
3. **Nuevas features** — crear carpetas en `src/feature/<nombre>/` siguiendo el patrón de `feature_1`.
4. **Nuevas pantallas** — agregar en `src/screens/` y registrar en `RootStack.js` o `TabNavigator.js`.

---

*Hecho con ❤️ por [matiudev](https://github.com/matiudev)*
