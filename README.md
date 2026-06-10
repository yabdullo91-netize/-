# FlowerShop — Интернет-магазин цветов

Полноценный интернет-магазин цветов с REST API, React-клиентом и Blazor-панелью администратора.

## Стек технологий

| Слой | Технологии |
|------|-----------|
| **API** | ASP.NET Core, Entity Framework Core, PostgreSQL |
| **Клиент** | React (Vite), TanStack Query, Zustand, Tailwind CSS, Framer Motion |
| **Админка** | Blazor WebAssembly |

## Структура репозитория

```
магазин цветов/
├── FlowerShop.API/           # REST API (ASP.NET Core)
│   ├── Controllers/          # HTTP-контроллеры
│   ├── Data/
│   │   ├── Configurations/   # EF Core конфигурации
│   │   └── Migrations/       # Миграции БД
│   ├── Models/
│   │   ├── DTOs/             # Data Transfer Objects
│   │   ├── Entities/         # Сущности БД
│   │   └── Enums/            # Перечисления
│   ├── Repositories/
│   │   ├── Interfaces/
│   │   └── Implementations/
│   ├── Services/
│   │   ├── Interfaces/
│   │   └── Implementations/
│   ├── Middleware/           # Глобальная обработка ошибок
│   ├── Mappings/             # AutoMapper профили
│   ├── Filters/              # Action/Exception фильтры
│   ├── Helpers/              # Утилиты
│   └── Extensions/           # Расширения DI
│
├── FlowerShop.Client/        # React-клиент
│   └── src/
│       ├── api/              # API-клиент (axios/fetch)
│       ├── assets/
│       │   ├── images/
│       │   └── styles/
│       ├── components/
│       │   ├── cart/         # Компоненты корзины
│       │   ├── catalog/      # Каталог и фильтры
│       │   ├── common/       # Shared UI (Button, Input, Toast…)
│       │   ├── layout/       # Header, Footer
│       │   ├── order/        # Оформление заказа
│       │   └── product/      # Карточка и страница товара
│       ├── context/          # React Context
│       ├── hooks/            # Кастомные хуки
│       ├── pages/            # Home, Catalog, Product, Cart, Checkout, Account
│       ├── store/            # Zustand stores (cart, favorites)
│       ├── types/            # TypeScript типы
│       └── utils/            # Утилиты
│
└── FlowerShop.Admin/         # Blazor-панель администратора
    ├── Components/
    │   ├── Charts/
    │   ├── Forms/
    │   ├── Modals/
    │   ├── Shared/
    │   └── Tables/
    ├── Pages/
    │   ├── Categories/
    │   ├── Customers/
    │   ├── Orders/
    │   ├── Products/
    │   └── Reports/
    ├── Services/
    │   ├── Interfaces/
    │   └── Implementations/
    ├── Helpers/
    ├── Layout/
    ├── Models/
    └── wwwroot/
```

## Быстрый старт

### Требования

- .NET 8 SDK
- Node.js 20+
- PostgreSQL 15+

### API

```bash
cd FlowerShop.API
dotnet restore
dotnet ef database update
dotnet run
```

API будет доступно на `https://localhost:7001`. Swagger UI — `/swagger`.

### Клиент (React)

```bash
cd FlowerShop.Client
npm install
npm run dev
```

Клиент запустится на `http://localhost:5173`.

### Админка (Blazor)

```bash
cd FlowerShop.Admin
dotnet restore
dotnet run
```

## Дизайн-система (клиент)

| Токен | Значение |
|-------|---------|
| Фон | `#FAF7F2` (тёплый off-white) |
| Акцент | `#1F4D3A` (глубокий зелёный) |
| Вторичный | `#E8B4B8` (пыльно-розовый) |
| Текст | `#1A1A1A` / `#6B6B6B` |
| Сетка | 4px base, max-w 1280px |
| Карточки | 2 / 3 / 4 колонки (mobile / tablet / desktop) |

Подробная спецификация фронтенда: [`flower-shop-frontend-spec.md`](./flower-shop-frontend-spec.md)

## Способы оплаты

- **Душанбе Сити (DC)** — редирект на платёжный шлюз
- **Алиф** — редирект на платёжный шлюз
- **Наличными курьеру**

## Команда

| Разработчик | Зона ответственности |
|-------------|---------------------|
| Abdullo | FlowerShop.API |
| Maruf | FlowerShop.Client |
| Muhammadsoleh | FlowerShop.Admin |

## Дедлайн

**13 июня 2026** — сдача MVP.

Приоритеты:
1. Каталог + карточка товара + фильтры
2. Корзина + checkout + интеграция DC/Алиф
3. Auth, избранное, отзывы, история заказов
