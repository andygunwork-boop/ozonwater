# Структура проекта ozonwater-landing

## Tech Stack
- **Framework**: Astro v4.15.0 — статический генератор сайтов (SSG), фокус на производительности и контент-сайты.
- **Язык**: TypeScript v5.5.0 — типизация, поддержка JSX (Astro/React-style).
- **Конфигурация**:
  - `astro.config.mjs`: Минимальная (static build по умолчанию).
  - `tsconfig.json`: Наследует `astro/tsconfigs/strict`, JSX для Astro компонентов.
- **Скрипты** (npm): `dev` (локальный сервер), `build` (генерация `dist/`), `preview` (просмотр билда).
- **Депенденции**: Только Astro + TS (no UI libs like React/Vue/Svelte).

**Общий обзор**: Минималистичный статический лендинг для "Ozon Water" (главная + privacy). Размер проекта мал, готов к деплою на любой статический хост (Netlify/Vercel/GitHub Pages).

## Иерархическая структура (tree)
Исключены служебные: `node_modules/` (зависимости), `.astro/` (кэш билда), `package-lock.json` (lockfile).

```
ozonwater/
├── .gitignore                 # Стандартные git-ignores (node_modules, dist и т.д.)
├── astro.config.mjs           # Astro config (defineConfig({}))
├── init                       # Пустой файл (возможно, shell-скрипт или placeholder)
├── package.json               # Зависимости и скрипты
├── tsconfig.json              # TS config
├── public/                    # Статические файлы (копируются в dist/)
│   ├── cran_bg_fruit.png      # Фоновое изображение (клюква/фрукты?)
│   └── ozonwater-bg2.png      # Фоновое изображение (ozonwater)
├── src/                       # Основной исходный код (Astro pages/components)
│   ├── env.d.ts               # TypeScript declarations (global env vars)
│   ├── layouts/               # Шаблоны layout
│   │   └── Layout.astro       # Базовый layout (header, footer, slots для страниц)
│   ├── pages/                 # Страницы (file-based routing)
│   │   ├── index.astro        # Главная страница лендинга
│   │   └── privacy.astro      # Страница политики конфиденциальности
│   └── styles/                # Стили (scoped/global CSS)
│       └── global.css         # Глобальные стили сайта
└── docs/                      # Документация (пустая на данный момент)
```

## Краткое описание ключевых файлов
- **package.json**: `dependencies: astro@^4.15.0`, `devDependencies: typescript@^5.5.0`.
- **astro.config.mjs**: Пустая конфигурация — использует дефолты (output: 'static').
- **tsconfig.json**: `extends: "astro/tsconfigs/strict"`, `jsx: "react-jsx"`, `jsxImportSource: "astro"`.
- **src/layouts/Layout.astro**: Общий шаблон для страниц (вероятно, содержит <head>, nav, main slot).
- **src/pages/index.astro & privacy.astro**: Содержимое страниц в Astro-синтаксисе (HTML + frontmatter).
- **src/styles/global.css**: Базовые CSS-правила (reset, typography, backgrounds).
- **public/**: Изображения загружаются как `/cran_bg_fruit.png` в билде.

Для запуска: `npm install && npm run dev`. Билд: `npm run build` → `./dist`.
