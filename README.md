<p align="center">
  <img src="public/img/brand/logo.svg" width="220" alt="Промет">
</p>

<h1 align="center">Конфигуратор шкафов Промет</h1>

<p align="center">
  <b>Веб-приложение для подбора, расчёта цены и оформления заказов на металлические шкафы-локеры серий ML и LS.</b>
</p>

<p align="center">
  Внутренний инструмент отдела продаж ООО «НПО Промет»: менеджер собирает конфигурацию шкафа, сразу видит цену, вес и срок изготовления и в один клик получает коммерческое предложение и наряд-заказ в PDF.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/React-19-61DAFB?logo=react&logoColor=black" alt="React 19">
  <img src="https://img.shields.io/badge/Vite-8-646CFF?logo=vite&logoColor=white" alt="Vite 8">
  <img src="https://img.shields.io/badge/Firebase-Auth_%2B_Firestore-FFCA28?logo=firebase&logoColor=black" alt="Firebase">
  <a href="https://github.com/dekciw/promet-lokers/releases/latest"><img src="https://img.shields.io/github/v/release/dekciw/promet-lokers?color=005EC4" alt="Release"></a>
  <a href="https://dekciw.github.io/promet-lokers/"><img src="https://img.shields.io/badge/GitHub_Pages-online-222222?logo=github&logoColor=white" alt="GitHub Pages"></a>
</p>

<p align="center">
  <a href="https://dekciw.github.io/promet-lokers/">
    <img src="https://img.shields.io/badge/Открыть_в_браузере-005EC4?style=for-the-badge" alt="Открыть в браузере">
  </a>
</p>

<br>

<p align="center">
  <img src="screenshot.png" width="900" alt="Экран конфигуратора: стандартное и нестандартное исполнение, итоговая конфигурация и параметры шкафа">
</p>

<br>

<table align="center">
  <tr>
    <td width="33%" valign="top">
      <h3>Конфигуратор</h3>
      <p>
        - Серия и модель из каталога<br>
        - Толщина металла корпуса и двери<br>
        - Габариты: ширина, высота, глубина<br>
        - Замок, вентиляция, цвет по RAL<br>
        - Сравнение со стандартным исполнением<br>
        - Цена, вес и срок изготовления сразу
      </p>
    </td>
    <td width="33%" valign="top">
      <h3>Документы</h3>
      <p>
        - Коммерческое предложение в PDF на фирменном бланке с фото модели<br>
        - Наряд-заказ в PDF с параметрами для производства<br>
        - История: к любой конфигурации можно вернуться и скачать документы заново
      </p>
    </td>
    <td width="33%" valign="top">
      <h3>Админ-панель</h3>
      <p>
        - Коэффициенты наценки по размерам, толщине, вентиляции и цвету<br>
        - Каталог: модели, фото, сортировка перетаскиванием<br>
        - Пользователи: роли и блокировка<br>
        - Вход по коду приглашения
      </p>
    </td>
  </tr>
</table>

<h3 align="center">Как это выглядит</h3>

<table align="center">
  <tr>
    <td align="center" valign="top"><img src="assets/screen-model.png" width="330" alt="Выбор модели шкафа из каталога серии ML"><br><sub>Выбор модели</sub></td>
    <td align="center" valign="top"><img src="assets/screen-params.png" width="330" alt="Собранная конфигурация, параметры и итоговая цена"><br><sub>Параметры и цена</sub></td>
    <td align="center" valign="top"><img src="assets/screen-mobile.png" width="120" alt="Мобильная версия: панель параметров"><br><sub>Мобильная версия</sub></td>
  </tr>
</table>

<p align="center">
  <sub>Конфигуратор и документы работают без регистрации. Вход нужен только для истории и админ-панели.</sub>
</p>

<br>

<details>
<summary><b>Подробнее о проекте: стек, устройство, расчёт цены, запуск</b> (нажми, чтобы развернуть)</summary>

<br>

## Содержание

- [Стек](#стек)
- [Устройство проекта](#устройство-проекта)
- [Расчёт цены](#расчёт-цены)
- [Запуск](#запуск)
- [Публикация](#публикация)
- [Дизайн](#дизайн)

## Стек

| Инструмент | Версия | Назначение |
|---|---|---|
| React | 19 | Интерфейс |
| Vite | 8 | Сборка и dev-сервер |
| Firebase | 12 | Авторизация и база данных Firestore |
| React Router | 7 | Маршрутизация |
| Motion | 12 | Анимации |
| pdf-lib + fontkit | 1.17 | Заполнение PDF-шаблонов КП и наряд-заказа |
| react-hook-form | 7 | Формы |
| @dnd-kit | 6 | Сортировка каталога перетаскиванием |
| sonner | 2 | Уведомления |
| Vitest, Testing Library | 2, 16 | Тесты |
| ESLint, knip | 9, 6 | Проверка кода |

Компоненты написаны с нуля на CSS Modules и CSS-переменных, без сторонних UI-библиотек.

## Устройство проекта

```
src/
├── pages/              # страницы: конфигуратор, админ-панель, история
├── modules/            # модули: Configurator, Parameters, Auth
├── shared/
│   ├── api/            # загрузка каталога из Firestore
│   ├── components/     # общие компоненты: шапка, модальные окна, уведомления
│   ├── context/        # общий контекст приложения
│   ├── hooks/          # хуки: каталог, история, конфигурация, админка
│   ├── lib/            # инициализация Firebase, загрузка фото
│   └── utils/          # расчёт цены, сравнение конфигураций, форматирование
└── pdf/
    ├── kp/             # коммерческое предложение
    └── nz/             # наряд-заказ
```

Каталог загружается из Firestore и кешируется в `localStorage` на 24 часа. Конфигурация живёт в состоянии приложения, а цена считается прямо в браузере в `calcPrice.js`, без запросов к серверу.

## Расчёт цены

```
цена = базовая цена × (1 + сумма коэффициентов доплат) + доплата за замок
```

Коэффициенты зависят от количества шкафов в заказе (от 1 до 100 и больше) и хранятся в Firestore, администратор меняет их в админ-панели. Если изменена ширина шкафа, цена считается вручную, и приложение подсказывает это менеджеру.

## Запуск

```bash
npm install
npm run dev        # dev-сервер
npm run build      # сборка
npm test           # тесты
npm run lint       # проверка кода
```

Для работы нужен файл `.env` с данными Firebase-проекта. Образец лежит в `.env.example`:

```
VITE_FIREBASE_API_KEY=...
VITE_FIREBASE_AUTH_DOMAIN=...
VITE_FIREBASE_PROJECT_ID=...
VITE_FIREBASE_STORAGE_BUCKET=...
VITE_FIREBASE_MESSAGING_SENDER_ID=...
VITE_FIREBASE_APP_ID=...
```

## Публикация

Сайт публикуется на GitHub Pages автоматически при каждом push в `main` (`.github/workflows/pages.yml`). Данные Firebase берутся из секретов репозитория с теми же именами, что и в `.env`.

## Дизайн

Макет интерфейса со всеми экранами и компонентами лежит в папке [`layout/`](./layout/) (файл Figma).

</details>

<br>

<p align="center">
  <sub>© 1991–2026 ООО «НПО Промет». Все права защищены.</sub>
</p>

<!-- Pull Shark 1 -->

<!-- Pull Shark 2 -->
