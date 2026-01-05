# csad-task1 
## 📊 Експорт даних з Google Таблиць (CI/CD)

Ми використовуємо Google Apps Script для автоматичного формування CSV файлу з вкладки "Список" та його завантаження в директорію `input/` цього репозиторію.

### Покрокова інструкція налаштування

#### Крок 1: Підготовка GitHub Token
Для того, щоб скрипт міг записувати дані у ваш репозиторій, потрібен токен доступу.
1. Перейдіть у [GitHub Developer Settings -> Personal access tokens (Classic)](https://github.com/settings/tokens).
2. Натисніть **Generate new token (classic)**.
3. Вкажіть ім'я (наприклад, `Google Sheets Integration`).
4. У розділі **Select scopes** обов'язково поставте галочку напроти **`repo`** (Full control of private repositories).
5. Згенеруйте токен та **скопіюйте його** (ви бачите його лише один раз).

#### Крок 2: Встановлення скрипта
1. Відкрийте Google Таблицю з даними груп.
2. Перейдіть у меню: `Розширення` (Extensions) -> `Apps Script`.
3. Відкриється редактор коду. Видаліть весь код у файлі `Code.gs`.
4. Відкрийте файл `ci/google_sheets_export.txt` з цього репозиторію, скопіюйте його вміст і вставте у редактор Google Apps Script.

#### Крок 3: Налаштування змінних
У редакторі скрипта знайдіть блок `CONFIGURATION` на початку файлу та замініть значення на ваші:

```javascript
  const GITHUB_TOKEN = 'ghp_xxxxxxxxxxxx';  // Ваш токен з Кроку 1
  const REPO_OWNER = 'username';            // Ваш нікнейм на GitHub
  const REPO_NAME = 'repo-name';            // Назва цього репозиторію
  const FILE_PATH = 'input/groups.csv';     // Шлях, куди зберегти файл
