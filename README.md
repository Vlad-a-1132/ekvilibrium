# Erich Krause Catalog

## Описание проекта
Интернет-каталог канцелярских товаров Erich Krause - современное веб-приложение на Next.js 14 с админ-панелью и полнофункциональным каталогом товаров.

## Технологии
- **Frontend**: Next.js 14, React 18, TypeScript
- **Backend**: Next.js API Routes
- **База данных**: PostgreSQL с Prisma ORM
- **Аутентификация**: NextAuth.js
- **Стили**: CSS Modules, Tailwind CSS
- **Развертывание**: Vercel

## Функционал

### Для пользователей:
- 📱 Адаптивный дизайн для всех устройств
- 🔍 Поиск и фильтрация товаров
- 📂 Категоризация товаров
- 🛒 Корзина покупок
- ❤️ Избранное
- 👤 Личный кабинет
- 📝 Блог с полезными статьями

### Для администраторов:
- 🛡️ Защищенная админ-панель
- 📦 Управление товарами (CRUD)
- 📁 Управление категориями
- 🖼️ Загрузка изображений
- 📊 Статистика

## Структура проекта

```
src/
├── app/
│   ├── admin/              # Админ-панель
│   ├── api/               # API маршруты
│   ├── catalog/           # Страницы каталога
│   ├── components/        # React компоненты
│   ├── context/          # React контексты
│   └── types/            # TypeScript типы
├── lib/                  # Утилиты и конфигурация
└── prisma/              # Схема базы данных
```

## Установка и запуск

### Предварительные требования
- Node.js 18+
- PostgreSQL
- npm или yarn

### Установка

1. Клонируйте репозиторий:
```bash
git clone https://github.com/Vlad-a-1132/ekvilibrium.git
cd ekvilibrium
```

2. Установите зависимости:
```bash
npm install
```

3. Настройте переменные окружения:
```bash
cp .env.example .env
```

Заполните `.env` файл:
```env
DATABASE_URL="postgresql://username:password@localhost:5432/erich_krause"
NEXTAUTH_SECRET="your-secret-key"
NEXTAUTH_URL="http://localhost:3000"
```

4. Настройте базу данных:
```bash
npx prisma db push
```

5. Создайте администратора:
```bash
node scripts/create-admin.js
```

6. Запустите проект:
```bash
npm run dev
```

## Доступ к админ-панели
- URL: `http://localhost:3000/admin/login`
- Email: `admin@example.com`
- Пароль: `admin123`

## Модели данных

### User (Пользователь)
- id, name, email, password
- role (USER | ADMIN)
- isActive, timestamps

### Category (Категория)
- id, name, slug, description
- order, isActive, timestamps

### Product (Товар)
- id, name, slug, description
- price, oldPrice, images[], sku
- stock, specifications (JSON)
- categoryId, isActive, timestamps

## API Endpoints

### Публичные
- `GET /api/categories` - Список категорий
- `GET /api/products` - Список товаров
- `GET /api/products/[id]` - Товар по ID

### Админ (требует аутентификации)
- `POST /api/admin/products` - Создание товара
- `PUT /api/admin/products/[id]` - Обновление товара
- `DELETE /api/admin/products/[id]` - Удаление товара
- `POST /api/admin/categories` - Создание категории
- `POST /api/admin/upload` - Загрузка изображений

## Развертывание

### Vercel
1. Подключите GitHub репозиторий к Vercel
2. Добавьте переменные окружения
3. Разверните проект

### Переменные окружения для продакшена:
```env
DATABASE_URL="your-production-db-url"
NEXTAUTH_SECRET="your-production-secret"
NEXTAUTH_URL="https://your-domain.com"
```

## Лицензия
MIT

## Поддержка
При возникновении вопросов создавайте Issues в репозитории.

---

**Разработчик**: [Vlad-a-1132](https://github.com/Vlad-a-1132)  
**Версия**: 1.0.0
