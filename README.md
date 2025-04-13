# План автоматизации тестирования формы записи на курс "Инженер по тестированию"

## 1. Автоматизируемые сценарии

### 1.1. Сценарии перехода к форме
```gherkin
Scenario: Переход через Каталог курсов
Given Пользователь на главной странице
When Выбирает "Каталог курсов" → "Программирование" → "Инженер по тестированию"
And Кликает на найденный курс
Then Открывается страница професии
And Кликает на кнопку "Записаться"

Scenario: Переход через поиск
Given Пользователь на главной странице
When Выбирает "Каталог курсов" → Вводит в поиск "Инженер по тестированию"
And Кликает на найденный курс
Then Открывается страница професии
And Кликает на кнопку "Записаться"

Scenario: Переход через карту действия (конпку) Освоить профессию
Given Пользователь на главной странице
When Кликает на карту действия (кнопку) Освоить профессию → "Программирование" → "Инженер по тестированию"
And Кликает на найденный курс
Then Открывается страница професии
And Скроллит всю страницу профессии до формы записи

Scenario: Переход через Смотреть курсы
Given Пользователь на главной странице
When Выбирает "Смотреть курсы" → "Программирование" → "Инженер по тестированию"
And Кликает на найденный курс
Then Открывается страница професии
And Кликает на кнопку "Записаться"
```
###  1.2. Сценарии заполнения формы
```gherkin
Scenario: Валидное заполнение
Given Пользователь на странице курса
When Заполняет поля:
  | Поле    | Значение        |
  | Имя     | Иван            |
  | Телефон | +79001234567    |
Then Кнопка "Записаться" активна

Scenario: Невалидный номер телефона
Given Пользователь на форме записи
When Вводит "invalid-phone" в поле Телефон
Then Поле подсвечивается красным
And под полем сообщение об ошибке "Неверный формат"

Scenario: Невалидное имя
Given Пользователь на форме записи
When Вводит "invalid-name" в поле Имя
Then Поле подсвечивается красным
And под полем сообщение об ошибке в соответствии тем, что было введено "Должно быть не короче 2 символов"/"Должно состять из букв"
```
### 2. Инструменты
1. **Selenide** - для UI-автоматизации
2. **JUnit 5** - как тестовый фреймворк
3. **Gradle** - для сборки
4. **Allure** - для отчетов

### 3. Необходимые разрешения
1. Доступ к тестовой среде (stage-версия сайта)
2. Mock-сервер для эмуляции отправки формы
3. Тестовые данные:
    * Телефонные номера

### 4. Риски
1. Изменение структуры страницы:
    * Mitigation: Использовать data-атрибуты для поиска элементов
2. Блокировка тестовых запросов:
    * Mitigation: Ограничить частоту выполнения тестов
3. Отсутствие тестовых данных:
    * Mitigation: Создать генератор тестовых данных

### 5. Команда
QA-инженер (1 чел.) - написание и поддержка тестов
DevOps-инженер - подготовка тестовой среды
Backend-разработчик - настройка Mock-сервер
### 6. Оценка времени

* Настройка окружения - 8 ч
* Написание тестов - 24 ч
* Интеграция отчетов - 4 ч
* Подготовка тестовых данных - 2 ч
* Настройка CI - 1 ч
* Итого: 39 ч (+20% = 8 ч резерв)