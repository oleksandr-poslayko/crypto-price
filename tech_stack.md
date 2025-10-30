# 🧱 Tech Stack

## 🌐 Frontend

**Framework:** Angular 
**Language:** TypeScript  
**Bundling / Tooling:** Angular CLI (стандартный)  
**CSS Preprocessor:** SCSS  
**State Management:** Signals + RxJS + Services  
**UI Components:** Angular Material  
**Notifications:** `MatSnackBar`  
**Charts / Visualization:** ApexCharts
- Поддерживает детализированный tooltip по наведению
- Имеет pie chart с отображением процентов от целого
- Гибкая и понятная API, современный внешний вид
- Хорошо интегрируется с Angular через официальную обёртку

**i18n:** не используется (на данном этапе)

---

## ⚙️ Backend

**Framework:** NestJS  
**Language:** TypeScript  
**Runtime:** Node.js  
**Auth:** JWT  
**ORM:** Prisma  
**Migrations:** Prisma Migrate  
**Logger:** Winston (интеграция с NestJS через признанное сообществом решение `nest-winston`)  
**External APIs:** CoinMarketCap API

**Redis / PubSub:** планируется позже  
**BullMQ (Background Jobs / Queues):** планируется позже

---

## 🧰 Infrastructure & DevOps

**Containerization:** Docker (обязательно для разработки и продакшена)  
**CI/CD:** GitHub Actions  
**Hosting (PaaS):** Render
- Минимум ручных настроек
- Бесплатный тариф для начала
- Возможность деплоя фронта и NestJS backend-а как отдельных сервисов
- Автоматическая интеграция с GitHub
- База данных PostgreSQL как managed service (Render Postgres)

---

## 🗄️ Database

**Database Engine:** PostgreSQL  
**Local (Dev):** PostgreSQL в Docker-контейнере  
**Production (Render):** Managed PostgreSQL от Render
- Миграции применяются при деплое через `npx prisma migrate deploy`
- Изменения структуры не теряют пользовательские данные
- Возможность безопасного расширения схемы

---

## 🚀 Развёртывание и миграции

### Локальная разработка

1. Изменяешь `schema.prisma`
2. Генерируешь и применяешь миграцию:
   ```bash
   npx prisma migrate dev --name <migration_name>
   ```
3. Тестируешь локально на контейнере PostgreSQL

### Продакшен (Render)

1. При деплое запускается команда:
```bash
  npx prisma migrate deploy 
```
2. Структура продовой базы синхронизируется без потери данных
