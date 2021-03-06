# Требования к разработке сайта на MODx (Artmebius)

### Основное ###

CMS:  **MODX Revolution последней релизной версии (на данный момент 2.8.1)**

Кодировка: ***UTF-8***

Рабочая папка проекта: **artmebius** (!)

Названия чанков, доп. полей (TV), файлов\папок должны быть написаны **латиницей**.

---

### Верстка ###

При разработке сайта должна быть обеспечена кроссбраузерность, при которой различие в отображении оформления сайта в разных браузерах минимально. Перечень поддерживаемых браузеров: **Google Chrome, Mozilla Firefox, Internet Explorer 11, Edge, Safari.**

**Верстку необходимо осуществлять с использованием препроцессора SCSS, можно использовать Bootstrap 4, jQuery 3+**

**Верстка должна быть адаптивной, валидной и корректно отображаться на устройствах с разрешением экрана от 320px**

**Шаблонизатор: Fenom**

---

### Общее ###

* Ссылки на внешние ресурсы должны открываться в новом окне (Соц. сети, др. сайты)
* На каждой странице должен быть H1 и только один
* seoTemplates - должен быть установлен и настроен на всех сайтах (Созданы поля: title, description, keywords)
* Пагинация: страницы ?page=1 в URL быть не должно. 1 страница по умолчанию главная в пагинации
* Canonical должен быть прописан на страницах с пагинацией.
* На страницах пагинации в категориях: 
    * не выводить описание категории (content); 
    * meta title = h1 + cтраница №...
    * meta description = h1 + страница №...
* В админке в доп. полях у всех ресурсов должна быть вкладка SEO с полями: H1, description, keywords, metaRobots
* metaRobots должны быть поля: (нет||noindex||nofollow||noindex,nofollow) в коде страницы не должен отображаться metarobots если не указано в админке.
* На атрибуты у ссылок ведущих на телефон и email (tel и mailto) должны быть прописаны на всем сайте
* В списках ресурсов (материалов, категорий, товаров) если у ресурса прописан menutitle то использовать его вместо pagetitle.
* Фильтр товаров: Должен фильтровать сперва по параметрам потом по цене. Должен фильтровать в любом случае, даже если у товара не указана цена.
* Google recaptcha 3 - на всех формах отправки писем (кроме в корзине).
* В формах обратной связи должен быть чекбокс "Согласен с политикой конфиденциальности" и ссылкой на политику конфиденциальности (даже если в макете форма нарисована без чекбокса)
* Поля в форме обратной связи, перед отправкой, должны быть проверены в соответствие с правилами валидации. Обязательные поля: имя, телефон. Телефон заполняется по маске +7(000)000-00-00.
* Проверить на отправку и доставку писем все формы обратной связи, оформление заказов и т.д.

---

### Файловая структура ###

***В корне сайта добавляются папки:***

```
- artmebius (тут ведется вся разработка)
    Пример структуры папки artmebius
    - chunks
    - connectors
    - css
    - fonts
    - img
    - js
    - plugins
    - scss
    - snippets
    - templates

- images (для картинок используемых на сайте: новости, товары, категории, бренды)
    - products (папка с изображениями товаров !!!)
    - categories (изображения категорий)
    - остальные папки по своему усмотрению
```
---

### Чанки ###

Все кастомные элементы (чанки, сниппеты, плагины) должны быть сохранены в виде статических файлов.

Основные блоки сайта (header, footer, sidebar и т.п) должны быть разбиты по чанкам. *Пример: /artmebius/chunks/ 

![](http://example.artmebius.ru/images/instructions/main_chunks.png)

Чанки должны быть логически сгруппированы по категориям, и в той же иерархии сохранены в виде статических файлов в рабочей папке проекта. 

Пример: *здесь чанки разбиты по категориям:*

![](http://example.artmebius.ru/images/instructions/group_chunks.png) 

*файловой системе создана такая же иерархия папок и файлов:*

![](http://example.artmebius.ru/images/instructions/group_chunks_fs.png)

---

### TV. Доп. поля ###

Вся более-менее динамическая информация (телефоны, слайдеры, преимущества, новости и т.п) должна быть легко управляема, и доступна в режиме менеджерского доступа (без доступа к редактированию чанков, шаблонов и т.п). Т.е. все элементы должны быть сделаны в виде TV - полей (телефоны, слайдеры, ...) или списка ресурсов (новости...). У пользователя, не знающего HTML не должно возникать проблем при управлении данными элементами. Все TV также должны быть разбиты по категориям .

*Пример:*

![](http://example.artmebius.ru/images/instructions/tv_example.png)

---

### Пакеты ###

Список всех установленных пакетов можно посмотреть здесь http://example.artmebius.ru/manager/?a=workspaces

**Ключевыми пакетами являются:**
* AjaxForm + Formit - формы обратной связи
* Gallery - галерея
* MIGX - ...
* pdoTools - ...
* seoTemplates - управление масками мета-тегов
* Tickets - отзывы
* translit - транслитерация алиасов
* Minishop2 + mSearch2 + msOptionsPrice2 - минишоп + поиск/фильтр + торговые предложения
* Shopkeeper + SimpleSearch + tagManager2 - шопкипер + поиск + фильтр

---

### Источники файлов ###
На сайте неободимо создать\настроить источники файлов: http://example.artmebius.ru/manager/?a=source
* *MS2 Images* - для изображений товаров (basePath: /images/products/)
* *Images* - для остальных изображений (basePath: /images/)
