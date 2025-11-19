# React Nested File Tree

## Drag-and-drop driven explorer for hierarchical datasets, built to highlight my approach to complex state orchestration in React + TypeScript projects and serve as a polished piece of my portfolio.

## "Исследователь иерархических наборов данных с функцией перетаскивания (drag-and-drop), созданный, чтобы продемонстрировать мой подход к оркестровке сложного состояния в проектах на React + TypeScript и послужить элементом моего портфолио."
Это описание проекта, который:
- Позволяет просматривать иерархические данные с помощью перетаскивания элементов.
- Призван показать навыки разработчика в управлении (оркестровке) сложным состоянием приложения.
- Написан с использованием технологий React и TypeScript.
- Является качественной, завершенной работой для включения в портфолио.

Документация представлена на двух языках: сначала русская версия, затем английская. Они содержат идентичный контент и следуют лучшим практикам оформления README для портфолио.

---

## 🇷🇺 Русская версия

### Живой проект
- Приложение: https://react-nested-file-tree.vercel.app/
- Репозиторий: https://github.com/AbayReushenov/react-nested-file-tree

### О проекте
- **Задача:** создать управляемый drag-and-drop интерфейс для сложных иерархий (файлы, сущности, оргструктуры) с защитой от логических ошибок.
- **Источник данных:** GitHub Gist, содержащий `entityLabelPages`. Поток данных: `transformEntityLabelPage` ➝ `createTree` ➝ загрузка через Redux-Saga.
- **Оркестрация состояния:** Redux Toolkit + вспомогательные функции гарантируют детерминированные мутации при перемещениях.
- **TypeScript-first:** строгая типизация API-контрактов, стора, компонентов и утилит минимизирует скрытые баги.

### Ключевые возможности
- Drag-and-drop на любом уровне вложенности с проверками на запрет циклов и переносов в самого себя.
- Панель подробностей автоматически синхронизируется с выбранным элементом и маршрутом (`/about/:id`).
- «Мягкое обновление» данных без перезагрузки страницы (кнопка Refresh).
- Иммутабельные операции удаления, обновления и перепривязки узлов.

### Архитектура
- **UI:** React 18 + React Router 6 (Trunk дерево + Sheet правая панель).
- **Drag mechanics:** нативные HTML5 события + guard-хелперы (`chekParentIds`, `cleanDropFromDragItem`).
- **State:** slice хранит `data`, `selected`, `selectedDrag`; мемоизированные селекторы ускоряют вычисления.
- **Async:** Redux-Saga перехватывает `getDataAsync`, получает данные и диспатчит `fillData`.
- **Pipeline данных:** нормализация → построение дерева → хранение в иммутабельных структурах.

### Структура проекта
```
src/
 ├─ api/                // получение данных и их трансформация
 ├─ store/              // Redux slice, селекторы, sagas, утилиты
 ├─ TreePage/           // разметка (Trunk + Sheet)
 ├─ Actions/            // футер с действиями (Refresh / Remove / Apply)
 └─ styles/             // модульные стили
```

### Быстрый старт
#### Требования
- Node.js 18+
- npm 8+

#### Установка
```bash
git clone https://github.com/AbayReushenov/react-nested-file-tree.git
cd react-nested-file-tree
npm install
```

#### Локальный запуск
```bash
npm start
```

#### Production-сборка
```bash
npm run build
```

#### Тесты
```bash
npm test
```

### Стек
- React 18 + TypeScript
- Redux Toolkit, Redux-Saga
- React Router v6
- React DnD (HTML5 backend)
- Axios, Bootstrap utilities

### Что интересно показать в портфолио
- **Функции работы с иерархией:** `createTree`, `removeById`, `update`, `chekParentIds` демонстрируют аккуратную работу с вложенными структурами.
- **Отделение асинхронного слоя:** Redux-Saga держит UI «тонким» и легко тестируемым.
- **Читаемая визуализация:** отступы рассчитываются динамически на основе глубины узла.
- **Готовность к расширению:** кнопка Apply может быть привязана к сохранению в API / БД без перестройки архитектуры.

### Контакты
- Абай Реушенов, Москва (UTC +03:00)
- Email: abay.reushenov@gmail.com
- GitHub: https://github.com/AbayReushenov
- Telegram: @Reushenov_Abay

---

## 🇺🇸 English version

### Live Demo
- App: https://react-nested-file-tree.vercel.app/
- Repository: https://github.com/AbayReushenov/react-nested-file-tree

### About The Project
- **Problem space:** build a safe drag-and-drop experience for deeply nested taxonomies (files, entities, org charts).
- **Data source:** a GitHub Gist with `entityLabelPages`. Flow: `transformEntityLabelPage` ➝ `createTree` ➝ hydrated via Redux-Saga.
- **State orchestration:** Redux Toolkit slice + helper utilities ensure deterministic drag/drop mutations.
- **TypeScript everywhere:** strict typing across the API layer, store, and UI surfaces hidden edge cases early.

### Key Features
- Multi-level drag-and-drop with guards that block self/descendant drops and avoid cyclic references.
- Detail panel synced with routing (`/about/:id`) for immediate context.
- Soft refresh button (no full reload) to restore pristine data from the gist.
- Immutable helpers for remove/update/re-parent operations.

### Architecture At A Glance
- **UI:** React 18 + React Router 6 (Trunk tree view + Sheet detail panel).
- **Interactions:** native HTML5 drag events plus guard helpers (`chekParentIds`, `cleanDropFromDragItem`).
- **State:** Redux Toolkit slice keeps `data`, `selected`, `selectedDrag`; selectors provide memoized views.
- **Async layer:** Redux-Saga listens to `getDataAsync` and dispatches `fillData` with normalized payloads.
- **Data pipeline:** normalize payload → build adjacency tree → store as immutable arrays.

### Project Structure
```
src/
 ├─ api/                // data fetching + transformers
 ├─ store/              // redux slice, selectors, sagas, helpers
 ├─ TreePage/           // layout (Trunk tree + Sheet details)
 ├─ Actions/            // footer controls (refresh / remove / debug)
 └─ styles/             // module CSS
```

### Getting Started
#### Prerequisites
- Node.js 18+
- npm 8+

#### Installation
```bash
git clone https://github.com/AbayReushenov/react-nested-file-tree.git
cd react-nested-file-tree
npm install
```

#### Local Development
```bash
npm start
```

#### Production Build
```bash
npm run build
```

#### Tests
```bash
npm test
```

### Tech Stack
- React 18 + TypeScript
- Redux Toolkit, Redux-Saga
- React Router v6
- React DnD (HTML5 backend)
- Axios, Bootstrap utilities

### Highlights Worth Showcasing
- **Hierarchy helpers:** `createTree`, `removeById`, `update`, and recursive guard functions keep tree mutations safe.
- **Saga-powered data flow:** async logic is separated cleanly from UI components.
- **Visual clarity:** indentation logic mirrors the depth of each node for instant readability.
- **Extensibility:** the Actions footer exposes a hook for persisting changes (“Apply”) to any backend.

### Contact
- Abay Reushenov, Moscow (UTC +03:00)
- Email: abay.reushenov@gmail.com
- GitHub: https://github.com/AbayReushenov
- Telegram: @Reushenov_Abay

Thanks for reading! Happy to walk you through the codebase or discuss integration ideas.
