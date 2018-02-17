# Подбор наиболее частный вопросов на собеседования для фронтэнда с ответами, чтобы освежить память

Пулреквесты с доп. вопросами и ответами приветствуются!

Очень полезные ресурсы для js:

Тут выучишь js: https://learn.javascript.ru/

А тут ты поймешь, что ты не знаешь js: http://dmitrysoshnikov.com/ecmascript/javascript-the-core-2nd-edition-rus

## Общие вопросы о веб-разработке:

- Можете ли пояснить разницу между progressive enhancement и graceful degradation?
	> graceful degradation будет пониматься как отказоустойчивость клиентских веб-интерфейсов.
	> Постепенная деградация может выражаться в возможности работы при отключённом JavaScript, в достаточно аккуратном отображении интерфейса в браузере, не поддерживающем новые свойства CSS3, в адекватном отображении сайта при отключенных изображениях. В каждом из этих случаев работа пользователя с интерфейсом будет в принципе возможна, хотя и не так удобна.

	> Что же такое progressive enhancement? Чаще всего этот термин переводят, как прогрессивное улучшение. Прогрессивное улучшение предполагает, что веб-интерфейсы должны создаваться поэтапно, циклически, от простого к сложному. На каждом из этапов должен получаться законченный веб-интерфейс, который будет лучше, красивее и удобнее предыдущего. Можно сказать, что сейчас таких этапов четыре:

	- «Старый-добрый-HTML»
	- «CSS»
	- «CSS3»
	- «JavaScript»

	> Источник: https://htmlacademy.ru/blog/7-progressive-enhancement

- Что такое feature detection (определение возможностей браузера)?
	> Feature detection определяет, поддерживает ли браузер тот или иной блок кода и запускает различный код в зависимости от того, поддерживает или нет, так чтобы браузер всегда мог показать рабочий код, вместо репортов об ошибках.

	> 2 способа определения в js:

	- распарсить юзер-агент, определить версию браузера и писать в коде свитчи по версии браузера
	- 
	```javascript
		if("geolocation" in navigator) {
			navigator.geolocation.getCurrentPosition(function(position) {
			// show the location on a map, perhaps using the Google Maps API
			});
		} else {
			// Give the user a choice of static maps instead perhaps
		}
	```

	> 1 способ в css:

	- @supports

	> Подробней: https://developer.mozilla.org/de/Learn/Tools_and_testing/Cross_browser_testing/Feature_detection

- Объясните, что означает "Семантическая разметка"
	> Семантическая вёрстка, или семантический HTML-код, — это подход к созданию веб-страниц на языке HTML, основанный на использовании HTML-тегов в соответствии с их семантикой (предназначением), а также предполагающий логичную и последовательную иерархию страницы. Он противопоставляется подходу, при котором написание HTML-кода определяется внешним видом веб-страницы. Для оформления веб-страниц, написанных в соответствии с семантикой, используются каскадные таблицы стилей (CSS). Стандарт HTML с самого начала включал в себя ряд семантических тегов, но большую популярность семантическая вёрстка получила после начала работ над HTML5.

	> Источник: https://ru.wikipedia.org/wiki/Семантическая_вёрстка

- Как можно оптимизировать загрузку внешних ресурсов на странице?
	1. Уменьшите количество HTTP-запросов
	2. Используйте поддомены для параллельного скачивания
	3. Используйте кэш браузера
	4. Используйте CDN для загрузки популярных JavaScript библиотек
	5. Используйте Gzip- сжатие

	> Подробней по каждому пункту: https://habrahabr.ru/post/137239/

- Каково преимущество в подгрузке внешних ресурсов с нескольких доменов?
	> Cогласно спецификации HTTP/1.1 на браузеры накладываются ограничения на количество одновременно загружаемых компонентов сайта, а именно не более 2-х компонентов с одного хоста. Поэтому если на Вашем сайте много графики, то ее лучше вынести на отдельный поддомен или поддомены. Для Вас это будет один и тот же сервер, а для браузера – разные. Чем больше поддоменов Вы создадите, тем больше файлов браузер сможет одновременно загрузить и тем быстрее загрузится вся страница сайта. Вам остается лишь изменить адрес картинок на новый. Очень простой, но действенный способ.

- Назовите три способа уменьшения времени загрузки страницы (воспринимаемого или реального)
	1. Помещайте CSS файлы в начале страницы
	2. Помещайте javascript в конец страницы
	3. Минимизируйте css и javascript
	4. Оптимизируйте ваши изображения
	5. Не масштабируйте изображения

	> Подробней по каждому пункту: https://habrahabr.ru/post/137239/

- Если Вы присоединились к проекту, где для форматирования используются табы, а Вы привыкли использовать пробелы, как Вы поступите?
	> Не спрашивайте, НИКОГДА!!!

- Что такое FOUC (Flash Of Unstyled Content)? Как его избежать?
	> Flash of Unstyled Content (FOUC) – это кратковременное появление неоформленных HTML-элементов в некоторых версиях браузеров – сразу же после создания визуальных элементов и до полного применения стилей CSS.
	> css {display: block} на компонент
	> В <head> инлайнится код, необходимый для показа минимум 600px высоты страницы без загрузки дополнительных стилей.

- Что такое критический путь рендеринга веб-страниц?
	> Критический путь рендеринга – это набор минимально необходимых для начала отрисовки страницы действий, ресурсов и вычислений.
	> Критический путь можно измерять в количестве критических ресурсов, минимальном времени загрузки (измеряется в RTT) и объеме критических ресурсов (в байтах).
	> Для иллюстрации возьмем простейший пример: HTML страницу размером 1 кб без внешних ресурсов. Критический путь будет: 1 ресурс (HTML-документ), 1 RTT (минимально), 1 кб трафика. Однако, таких простых страниц в природе почти не встретить, поэтому покажем, как можно определять критический путь на реальных веб-страницах.

	> Подробней: https://habrahabr.ru/post/262239/

- Что такое WebSQL?
	> WebSQL DB — это API для доступа к полноценному SQL-хранилищу данных, основанному на SQLite. Впрочем, последнее обстоятельство — скорее, особенность реализации и стандартом не оговаривается, хотя диалект SQL используется именно от SQLite.

	> Подробней:

	- (en) https://developer.mozilla.org/en-US/docs/Mozilla/Tech/XPCOM/Storage
	- https://habrahabr.ru/post/84654/
	- (Раздел: За пределами пары ключ/значение: конкурентное видение) http://htmlbook.ru/html5/storage

- Является ли WebSQL частью спецификации HTML 5?
	> Нет. Многие относят его к HTML 5, но WebSQL не является частью спецификации HTML 5. Спецификация основана на SQLite.

	> Поддержка браузерами: https://caniuse.com/#search=websql

## Вопросы по HTML:

- Для чего нужен doctype и сколько разновидностей Вы можете назвать?
	> Элемент <!DOCTYPE> предназначен для указания типа текущего документа — DTD (document type definition, описание типа документа). Это необходимо, чтобы браузер понимал, как следует интерпретировать текущую веб-страницу, поскольку HTML существует в нескольких версиях, кроме того, имеется XHTML (EXtensible HyperText Markup Language, расширенный язык разметки гипертекста), похожий на HTML, но различающийся с ним по синтаксису. Чтобы браузер «не путался» и понимал, согласно какому стандарту отображать веб-страницу и необходимо в первой строке кода задавать <!DOCTYPE>.

	> HTML 4.01
	> HTML 5
	> XHTML 1.0
	> XHTML 1.1

	> Подробней про то, как указывать теги для определенного Doctype: http://htmlbook.ru/html/%21doctype
	> Хорошая полезная подробная статья: https://habrahabr.ru/post/71364/

- Что такое режим совместимости (Quirks Mode) и стандартный режим (Standards Mode)
	> На сегодняшний день существует три режима отображения, которые используются движками разметки (layout engines) браузеров: режим совместимости (quirks mode), частично стандартный режим (almost standards mode) и стандартный режим (full standards mode). В режиме совместимости (quirks mode), разметка эмулирует нестандартное поведение браузеров Navigator 4 и Internet Explorer 5. Этот режим необходим для поддержки сайтов, созданных до начала широкого применения веб стандартов. В стандартном режиме (full standards mode) поведение браузера соответствует (будем надеяться) описанному в спецификациях HTML и CSS. В частично стандартном режиме (almost standards mode)  реализовано лишь незначительное количество так называемых "странностей" (quirks).

	> Если вы будете пользоваться неполным тегом DOCTYPE, устаревшим его видом, или вообще забудете про него, броузер перейдет в «загадочный» (quirk) режим и будет исходить из предположения, что вы писали код страницы с ошибками и вольно отступали от стандартов, т.е. так, как писали в конце 90-ых годов.  В этом режиме броузер попытается разобрать вашу страницу по правилам обратной совместимости и выведет на экран, например, CSS так, как его вывел бы Internet Explorer 4-ой версии, а DOM будет работать так, как он работал именно в этом броузере (IE переключается в свой старый DOM, а Mozilla и Netscape 6 переключается вообще в бог знает что).

	> Подробней: https://developer.mozilla.org/ru/docs/Web/HTML/Quirks_Mode_and_Standards_Mode
	> Подробней: https://habrahabr.ru/post/71364/

- В чем разница между HTML и XHTML?
	> XHTML - это приложение XML, которое является довольно строгим языком с угловыми скобками.
	> HTML - это приложение SGML, которое является гораздо менее строгим языком с угловой скобкой.
	> (XML также является применением SGML.)

	> При написании кода XHTML придерживаются того же синтаксиса, который характерен для HTML. При этом разница между HTML и XHTML состоит в наборе некоторых обязательных правил.

	> Правила XHTML следующие.

	1. Все теги и их атрибуты должны быть набраны в нижнем регистре (строчными символами).
	2. Значения любых атрибутов необходимо заключать в кавычки.
	3. Требуется закрывать все теги, даже такие, которым не сопоставлен закрывающий тег.
	4. Должна соблюдаться правильная вложенность тегов.
	5. Нельзя использовать сокращенные атрибуты тегов.
	6. Вместо атрибута name следует указывать id.
	7. Следует определять DTD (document type definition, описание типа документа) с помощью элемента <!DOCTYPE>.

	> Подробнее с примерами: http://htmlbook.ru/xhtml/sintaksis-xhtml

- Могут ли возникнуть проблемы при подаче страниц с типом application/xhtml+xml?
	> MIME (Multipurpose Internet Mail Extensions, многоцелевые расширения интернет-почты) — стандарт Интернет, является частью протокола HTTP. Задача MIME это идентификация типа содержимого документа по его заголовку. К примеру, текстовый файл имеет тип text/plain, а HTML-файл — text/html. Отправка заголовка обычно происходит на основе расширения файла веб-сервером.
	> Документы XHTML по умолчанию отправляются как text/html, что в действительности говорит о том, что мы имеем дело с HTML, а не XHTML-файлом. Чтобы задействовать возможности XHTML требуется отдавать файл с типом application/xhtml+xml. Если у вас установлен веб-сервер Apache, то вы можете сделать это через директиву AddType, добавив следующую строку в файл .htaccess, расположенный в корне сайта.

	```AddType application/xhtml+xml .xhtml```

	> В данном случае мы говорим, что все файлы с расширением .xhtml отдавать как application/xhtml+xml. Если документы формируются через PHP, то можно отдавать заголовок следующим образом:

	```header ("Content-type: application/xhtml+xml");```

	> чтите, что эта строка должна идти до вывода любого текста на странице.
	> Браузер Internet Explorer до версии 8.0 включительно не поддерживает тип application/xhtml+xml и не сможет отобразить страницу, которая отдаётся с этим типом. Остальные браузеры, в том числе IE9, понимают этот тип как переход в стандартный режим.
	> Тип application/xhtml+xml необходим в случае, когда в документе применяется MathML (Mathematical Markup Language, язык математической разметки), предназначенный для добавления формул или SVG (Scalable Vector Graphics, масштабируемая векторная графика), язык разметки для создания на странице векторных рисунков. Если вы ничего не знаете об этих технологиях и пока не собираетесь их использовать, лучше отдавать документ как text/html. Это позволит охватить наибольшее количество браузеров и поисковых систем.
	> По сути, тип text/html для файлов с расширением .html или .htm настроен автоматически, поэтому не требуется предпринимать каких-либо действий для этого типа.

	> согласование содержимого для переключения между application/xhtml+xml и text/html так же, как вы описываете, не замечая проблем с поисковыми роботами. Строго говоря, вы должны учитывать значения q в заголовке accept, который указывает предпочтение пользовательского агента к каждому типу контента. Если пользовательский агент предпочитает принимать text/html, но будет принимать application/xhtml+xml в качестве альтернативы, то для обеспечения максимальной безопасности вы должны иметь страницу text/html.

- Как следует оформлять страницу, в которой контент может быть на разных языках?
	> От гугла: https://support.google.com/webmasters/answer/182192?hl=ru

- Чем полезны data- атрибуты?
	> HTML5 спроектирован с возможностью расширения данных ассоциированных с каким-либо элементом, но в то же время не обязательно имеющих определённое значение. data-* атрибуты позволяют хранить дополнительную информацию в стандартных элементах HTML, без хаков вроде нестандартных атрибутов, лишних DOM-свойств или Node.setUserData().

	> Синтаксис HTML
	```html
	<article
		id="electriccars"
		data-columns="3"
		data-index-number="12314"
		data-parent="cars">
	</article>
	```

	> Доступ в JavaScript
	```javascript
	var article = document.getElementById('electriccars');
	article.dataset.columns // "3"
	article.dataset.indexNumber // "12314"
	article.dataset.parent // "cars"
	```

	> Доступ в CSS
	```css
	article::before {
		content: attr(data-parent);
	}
	```

	> Подробнее: https://developer.mozilla.org/ru/docs/Web/Guide/HTML/Using_data_attributes

- Если рассматривать HTML5 как открытую web-платформу, на чем она строится, из каких компонентов состоит?
	> HTML5 (англ. HyperText Markup Language, version 5) — язык для структурирования и представления содержимого всемирной паутины. Это пятая версия HTML. Хотя стандарт был завершён (рекомендованная версия к использованию) только в 2014 году (предыдущая, четвёртая, версия опубликована в 1999 году), ещё с 2013 года[4] браузерами оперативно осуществлялась поддержка, а разработчиками — использование рабочего стандарта (англ. HTML Living Standard). Цель разработки HTML5 — улучшение уровня поддержки мультимедиа-технологий с одновременным сохранением обратной совместимости, удобочитаемости кода для человека и простоты анализа для парсеров.

	> Во всемирной паутине долгое время использовались стандарты HTML 4.01, XHTML 1.0 и XHTML 1.1. Веб-страницы на практике оказывались свёрстаны с использованием смеси особенностей, представленных различными спецификациями, включая спецификации программных продуктов, например веб-браузеров, а также сложившихся общеупотребительных приёмов. HTML5 был создан как единый язык разметки, который мог бы сочетать синтаксические нормы HTML и XHTML. Он расширяет, улучшает и рационализирует разметку документов, а также добавляет единый API для сложных веб-приложений.

	> В HTML5 реализовано множество новых синтаксических особенностей. Например, элементы <video>, <audio> и <canvas>, а также возможность использования SVG и математических формул. Эти новшества разработаны для упрощения создания и управления графическими и мультимедийными объектами в сети без необходимости использования сторонних API и плагинов. Другие новые элементы, такие как <section>, <article>, <header> и <nav>, разработаны для того, чтобы обогащать семантическое содержимое документа (страницы). Новые атрибуты были введены с той же целью, хотя ряд элементов и атрибутов был удалён. Некоторые элементы, например <a>, <menu> и <cite>, были изменены, переопределены или стандартизированы. API и DOM стали основными частями спецификации HTML5. HTML5 также определяет некоторые особенности обработки ошибок вёрстки, поэтому синтаксические ошибки должны рассматриваться одинаково всеми совместимыми браузерами.

	> Подробнее: https://ru.wikipedia.org/wiki/HTML5

- В чем отличия HTML5 от HTML4.01 и XHTML1.0
	> Ниже представлен список отличий(не все):

	- Изменён синтаксис
	- Встраивание SVG и MathML в text/html
	- Новые элементы: ```<article>, <aside>, <audio>, <canvas>, <command>, <datalist>, <details>, <embed>, <figcaption>, <figure>, <footer>, <header>, <hgroup>, <keygen>, <main>, <mark>, <meter>, <nav>, <output>, <progress>, <rp>, <rt>, <ruby>, <section>, <source>, <summary>, <time>, <video>, <wbr>```
	- Новые компоненты ввода: ```date/time, email, url, search, number, range, tel, color```
	- Новые атрибуты: charset (в ```<meta>```), async (в script)
	- Глобальные атрибуты, которые могут быть применены ко всем элементам: id, tabindex, hidden, data-* (пользовательские атрибуты данных)
	- Элементы, которые будут исключены: ```<acronym>, <applet>, <basefont>, <big>, <center>, <dir>, <font>, <frame>, <frameset>, <isindex>, <noframes>, <strike>, <tt>```

	> Подробнее: https://ru.wikipedia.org/wiki/HTML5

- Объясните разницу между cookies, sessionStorage и localStorage.
	- LocalStorage

		Плюсы:
		- Веб-хранилище можно рассматривать упрощенно как усовершенствование файлов cookie, обеспечивая гораздо большую емкость хранилища. Если вы посмотрите исходный код Mozilla, мы увидим, что 5120KB (5 МБ), равный 2,5 миллионам символов в Chrome), является размером хранилища по умолчанию для весь домен. Это дает вам значительно больше возможностей для работы, чем обычный cookie 4 КБ.
		- Данные не отправляются обратно на сервер для каждого HTTP-запроса (HTML, изображения, JavaScript, CSS и т.д.) - уменьшение количества трафика между клиентом и сервером.
		- Данные, хранящиеся в localStorage, сохраняются до явного удаления. Сделанные изменения сохраняются и доступны для всех текущих и будущих посещений сайта.

		Минусы:
		- Он работает в политике одного и того же происхождения. Таким образом, сохраненные данные будут доступны только в том же месте.

	- Cookies

		Плюсы:
		- По сравнению с другими, ничего.

		Минусы:
		- Предел 4K предназначен для всего файла cookie, включая имя, значение, дату истечения срока годности и т.д. Чтобы поддерживать большинство браузеров, держите имя менее 4000 байт и общий размер файла cookie под 4093 байтами.
		- Данные отправляются обратно на сервер для каждого HTTP-запроса (HTML, изображения, JavaScript, CSS и т.д.) - увеличение количества трафика между клиентом и сервером.

		Обычно допустимы следующие действия:
		- 300 файлов cookie
		- 4096 байт для каждого файла cookie
		- 20 файлов cookie для каждого домена
		- 81920 байт для каждого домена (задано 20 файлов cookie максимального размера 4096 = 81920 байт.)

	- sessionStorage

		Плюсы:
		- Он похож на localStorage.
		- Изменения доступны только для каждого окна (или вкладки в браузерах, таких как Chrome и Firefox). Сделанные изменения сохраняются и доступны для текущей страницы, а также для будущих посещений сайта в том же окне. Когда окно закрыто, хранилище удаляется.

		Минусы:
		- Данные доступны только внутри окна/вкладки, в котором он был установлен.
		- Данные не сохраняются, т.е. будут потеряны после закрытия окна/вкладки.
		- Подобно localStorage, работает в политике одинакового происхождения. Таким образом, сохраненные данные будут доступны только в том же месте.

	> Подробней:
	
	- LocalStorage: https://developer.mozilla.org/ru/docs/Web/API/Window/localStorage
	- Cookies: https://developer.mozilla.org/ru/docs/Web/HTTP/Куки
	- SessionStorage: https://developer.mozilla.org/ru/docs/Web/API/Window/sessionStorage