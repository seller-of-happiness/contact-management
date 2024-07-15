# Contact Management

Приложение для управления контактами, созданное с использованием Vue 3, Composition API, TypeScript, Tailwind CSS и Pug.

## Setup

1. Клонируйте репозиторий:

```bash
# yarn
yarn install

# npm
npm install

# pnpm
pnpm install
```

## Development Server

Start the development server on `http://localhost:3000`

```bash
npm run dev
```

## Production

Build the application for production:

```bash
npm run build
```

Locally preview production build:

```bash
npm run preview
```


## Технологии
- **Vue 3**: Фреймворк для создания пользовательских интерфейсов.
- **Composition API**: Новый способ написания логики компонентов во Vue 3.
- **TypeScript**: Надстройка над JavaScript, добавляющая статическую типизацию.
- **Tailwind CSS**: Утилитарный CSS-фреймворк для быстрой и удобной стилизации.
- **Pug**: Шаблонизатор для упрощения написания HTML.

## Функциональность
- **Добавление контактов**: Возможность добавлять новые контакты с именем и телефоном.
- **Редактирование контактов**: Возможность редактировать существующие контакты.
- **Удаление контактов**: Возможность удалять контакты.
- **Поиск контактов**: Возможность искать контакты по имени.
- **Хранение данных в `localStorage`**: Все контакты сохраняются в `localStorage`, что позволяет сохранять данные между сеансами.
- **Валидация формы**: Проверка корректности введенных данных.
