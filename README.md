# План автоматизации тестирования формы записи на курс "Инженер по тестированию"

## 1. Автоматизируемые сценарии

### 1.1. Сценарии перехода к форме

**Сценарий 1**: Переход к форме записи через каталог курсов

1. Пользователь открывает главную страницу
2. Нажимает на раздел "Каталог курсов"
3. Выбирает категорию "Программирование"
4. Выбирает курс "Инженер по тестированию"
5. На странице курса нажимает кнопку "Записаться"
   * _Ожидаемый результат_: Открывается форма записи на курс

**Сценарий 2**: Переход к форме записи через поиск

1. Пользователь открывает главную страницу
2. Нажимает на раздел "Каталог курсов"
3. Вводит в поиск "Инженер по тестированию"
4. Выбирает найденный курс из результатов поиска
5. На странице курса нажимает кнопку "Записаться"
   * _Ожидаемый результат_: Открывается форма записи на курс

**Сценарий 3**: Переход к форме записи через карточку действия
1. Пользователь открывает главную страницу
2. Нажимает на карточку "Освоить профессию"
3. Выбирает категорию "Программирование"
4. Выбирает курс "Инженер по тестированию"
5. На странице курса прокручивает до формы записи
   * _Ожидаемый результат_: Форма записи на курс отображается на странице

**Сценарий 4**: Переход к форме записи через кнопку "Смотреть курсы"

1. Пользователь открывает главную страницу
2. Нажимает на раздел "Смотреть курсы"
3. Выбирает категорию "Программирование"
4. Выбирает курс "Инженер по тестированию"
5. На странице курса нажимает кнопку "Записаться"
   * _Ожидаемый результат_: Открывается форма записи на курс

###  1.2. Сценарии заполнения формы

**Сценарий 5**: Успешная отправка формы с валидными данными на кириллице

1. Пользователь открывает форму записи
2. Заполняет поле "Имя" валидным значением (2+ кириллических символа. Возможно двойное имя через "-". Без использования цифр и прочих специальных символов)
   _Пример_: "Иван-младший"
3. Заполняет поле "Телефон" валидным номером (префикс +7, 11 цифр, без использования букв и специальных символов)
   _Пример_: "+79123456789"
4. Нажимает кнопку "Записаться"
   * Ожидаемый результат: Форма успешно отправляется, появляется сообщение об успешной записи

**Сценарий 6**: Успешная отправка формы с валидными данными на латинице

1. Пользователь открывает форму записи
2. Заполняет поле "Имя" валидным значением (2+ латинских символа. Возможно двойное имя через "-". Без использования цифр и прочих специальных символов)
   _Пример_: "John-Smith"
3. Заполняет поле "Телефон" валидным номером (префикс +7, 11 цифр, без использования букв и специальных символов)
   _Пример_: "+79123456789"
4. Нажимает кнопку "Записаться"
   * Ожидаемый результат: Форма успешно отправляется, появляется сообщение об успешной записи

**Сценарий 7**: Попытка отправки формы с десятизначным телефоном

1. Пользователь открывает форму записи
2. Заполняет поле "Имя" валидным значением (2+ кириллических/латинских символа. Возможно двойное имя через "-". Без использования цифр и прочих специальных символов)
   _Пример_: "Иван-Сергей"
3. Заполняет поле "Телефон" невалидным значением (менее 11 цифр)
   _Пример_: "+7912345678"
4. Нажимает кнопку "Записаться"
   * Ожидаемый результат: Поле "Телефон" подсвечивается как ошибочное, отображается сообщение "Неверный формат", форма не отправляется

**Сценарий 8**: Попытка отправки формы с двенадцатизначным телефоном

1. Пользователь открывает форму записи
2. Заполняет поле "Имя" валидным значением (2+ кириллических/латинских символа. Возможно двойное имя через "-". Без использования цифр и прочих специальных символов)
   _Пример_: "Иван-Сергей"
3. Заполняет поле "Телефон" невалидным значением (более 11 цифр)
   _Пример_: "+791234567899"
4. Нажимает кнопку "Записаться"
   * Ожидаемый результат: Поле "Телефон" подсвечивается как ошибочное, отображается сообщение "Неверный формат", форма не отправляется

**Сценарий 9**: Попытка отправки формы с телефоном без префикса РФ

1. Пользователь открывает форму записи
2. Заполняет поле "Имя" валидным значением (2+ кириллических/латинских символа. Возможно двойное имя через "-". Без использования цифр и прочих специальных символов)
   _Пример_: "Иван-Сергей"
3. Заполняет поле "Телефон" невалидным значением (без +7)
   _Пример_: "9123456789"
4. Нажимает кнопку "Записаться"
   * Ожидаемый результат: Поле "Телефон" подсвечивается как ошибочное, отображается сообщение "Неверный формат", форма не отправляется

**Сценарий 10**: Попытка отправки формы с буквой в номере телефона

1. Пользователь открывает форму записи
2. Заполняет поле "Имя" валидным значением (2+ кириллических/латинских символа. Возможно двойное имя через "-". Без использования цифр и прочих специальных символов)
   _Пример_: "Иван-Сергей"
3. Заполняет поле "Телефон" невалидным значением (c использованием букв)
   _Пример_: "+7912345678ж"
4. Нажимает кнопку "Записаться"
   * Ожидаемый результат: Поле "Телефон" подсвечивается как ошибочное, отображается сообщение "Неверный формат", форма не отправляется

**Сценарий 11**: Попытка отправки формы со специальным символом в номере телефона

1. Пользователь открывает форму записи
2. Заполняет поле "Имя" валидным значением (2+ кириллических/латинских символа. Возможно двойное имя через "-". Без использования цифр и прочих специальных символов)
   _Пример_: "Иван-Сергей"
3. Заполняет поле "Телефон" невалидным значением (c использованием специальных символов)
   _Пример_: "+79123%56789"
4. Нажимает кнопку "Записаться"
   * Ожидаемый результат: Поле "Телефон" подсвечивается как ошибочное, отображается сообщение "Неверный формат", форма не отправляется

**Сценарий 12**: Попытка отправки формы с именем состоящим из одной буквы

1. Пользователь открывает форму записи
2. Заполняет поле "Имя" невалидным значением (1 символ)
   _Пример_: "А"
3. Заполняет поле "Телефон" валидным номером (префикс +7, 11 цифр, без использования букв и специальных символов)
   _Пример_: "+79123456789"
4. Нажимает кнопку "Записаться"
   * Ожидаемый результат: Поле "Имя" подсвечивается как ошибочное, отображается сообщение об ошибке "Должно быть не короче 2 символов", форма не отправляется

**Сценарий 13**: Попытка отправки формы с именем состоящим из иероглифов

1. Пользователь открывает форму записи
2. Заполняет поле "Имя" невалидным значением (иероглифы)
   _Пример_: "安德烈"
3. Заполняет поле "Телефон" валидным номером (префикс +7, 11 цифр, без использования букв и специальных символов)
   _Пример_: "+79123456789"
4. Нажимает кнопку "Записаться"
   * Ожидаемый результат: Поле "Имя" подсвечивается как ошибочное, отображается сообщение об ошибке "Должно состоять из букв", форма не отправляется

**Сценарий 14**: Попытка отправки формы с именем из некириллических и нелатинских букв

1. Пользователь открывает форму записи
2. Заполняет поле "Имя" невалидным значением (не кириллические или не латинские буквы)
   _Пример_: "ანდრეი"
3. Заполняет поле "Телефон" валидным номером (префикс +7, 11 цифр, без использования букв и специальных символов)
   _Пример_: "+79123456789"
4. Нажимает кнопку "Записаться"
   * Ожидаемый результат: Поле "Имя" подсвечивается как ошибочное, отображается сообщение об ошибке "Должно состоять из букв", форма не отправляется

**Сценарий 15**: Попытка отправки формы с именем из букв и цифр

1. Пользователь открывает форму записи
2. Заполняет поле "Имя" невалидным значением (латинские или кириллические буквы и цифры)
   _Пример_: "Егор12"
3. Заполняет поле "Телефон" валидным номером (префикс +7, 11 цифр, без использования букв и специальных символов)
   _Пример_: "+79123456789"
4. Нажимает кнопку "Записаться"
   * Ожидаемый результат: Поле "Имя" подсвечивается как ошибочное, отображается сообщение об ошибке "Должно состоять из букв", форма не отправляется

**Сценарий 16**: Попытка отправки формы с именем из букв и специальных символов

1. Пользователь открывает форму записи
2. Заполняет поле "Имя" невалидным значением (латинские или кириллические буквы и специальные символы)
   _Пример_: "(@ша"
3. Заполняет поле "Телефон" валидным номером (префикс +7, 11 цифр, без использования букв и специальных символов)
   _Пример_: "+79123456789"
4. Нажимает кнопку "Записаться"
   * Ожидаемый результат: Поле "Имя" подсвечивается как ошибочное, отображается сообщение об ошибке "Должно состоять из букв", форма не отправляется

### 2. Инструменты
1. **Java 11**
_Базовый язык для написания тестов_

   ✓ Поддержка всех современных библиотек

2. **Selenide**
_Фреймворк для UI-автоматизации_

   ✓ Автоматические ожидания элементов

   ✓ Лёгкий синтаксис ($("#element").click())

3. **JUnit 5**
_Тестовый фреймворк_

   ✓ Параметризованные тесты (@ParameterizedTest)

   ✓ Гибкие аннотации (@BeforeEach, @DisplayName)

4. **Lombok**
_Библиотека для сокращения boilerplate-кода_

   ✓ Генерация геттеров/сеттеров через

   ✓ Автозаполнение конструкторов

   ✓ Логирование через

5. **JavaFaker**
_Генератор реалистичных тестовых данных_

   ✓ Поддержка локалей (русские имена/телефоны)
   
   ✓ Простое использование

6. **Gradle + Allure**
_Сборка и отчёты_

   ✓ Плагин allure-gradle для отчётов
   
   ✓ Фильтрация тестов по тегам

### 3. Необходимые разрешения
1. Доступ к тестовой среде (stage-версия сайта)
2. Mock-сервер для эмуляции отправки формы
3. Тестовые данные:
   * Валидные имена: кириллица/латиница 2+ символа, двойные имена через "-"
   * Невалидные имена: спецсимволы, 1 символ
   * Телефоны: валидные (+7XXXXXXXXXX) и невалидные

### 4. Риски
1. Изменение структуры страницы:
    * Mitigation: Использовать data-атрибуты для поиска элементов
2. Блокировка тестовых запросов:
    * Mitigation: Ограничить частоту выполнения тестов
3. Отсутствие тестовых данных:
    * Mitigation: Создать генератор тестовых данных

### 5. Команда
**Исполнитель**: QA Automation Engineer (1 человек)
### 6. Оценка времени

* Настройка окружения - 6 ч
* Добавление Lombok/Faker - 2 ч
* Написание тестов - 15 ч
* Интеграция отчетов - 3 ч
* Подготовка тестовых данных - 2 ч
* Настройка CI - 1 ч
* Итого: 29 ч (+20% = 6 ч резерв)