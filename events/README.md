# События(events)

## Темы
- [x] Структура DOM
- [x] Усложнённые селекторы
  - [x] Селектор потомка
  - [x] Дочерний селектор
  - [x] Сестринский селектор
  - [x] Селектор атрибута
- [ ] Селектор псевдокласса
  - [ ] link/visited
  - [ ] focus
  - [ ] hover
  - [ ] active

## Структура DOM

Элементы, находящиеся внутри элемента \<html>, образуют дерево документа, так называемую объектную модель документа, DOM (document object model). При этом элемент \<html> является корневым элементом.

![DOM](./asserts/DOM.png)

Чтобы разобраться во взаимодействии элементов веб-страницы, необходимо рассмотреть так называемые «родственные отношения» между элементами. Отношения между множественными вложенными элементами подразделяются на родительские, дочерние и сестринские.

Предок — элемент, который заключает в себе другие элементы. На рисунке 1 предком для всех элементов является \<html>. В то же время элемент \<body> является предком для всех содержащихся в нем элементов: \<h1>, \<p>, \<span>, \<nav> и т.д.
Потомок — элемент, расположенный внутри одного или более типов элементов. Например, \<body> является потомком \<html>, а элемент \<p> является потомком одновременно для \<body> и \<html>.
Родительский элемент — элемент, связанный с другими элементами более низкого уровня, и находящийся на дереве выше их. На рисунке 1 \<html> является родительским только для \<head> и \<body>. Элемент \<p> является родительским только для \<span>.
Дочерний элемент — элемент, непосредственно подчиненный другому элементу более высокого уровня. На рисунке 1 только элементы \<h1>, \<h2>, \<p> и \<nav> являются дочерними по отношению к \<body>.
Сестринский элемент — элемент, имеющий общий родительский элемент с рассматриваемым, так называемые элементы одного уровня. На рисунке 1 \<head> и \<body> — элементы одного уровня, так же как и элементы \<h1>, \<h2> и \<p> являются между собой сестринскими.

## Сложные селекторы

### Селектор потомка

Селекторы потомков применяют стили к элементам, расположенным внутри элемента-контейнера. Например, ul li {text-transform: uppercase;} — выберет все элементы li, являющиеся потомками всех элементов ul.

Если нужно отформатировать потомки определенного элемента, этому элементу нужно задать стилевой класс:

- ```p.first a {color: green;}``` — данный стиль применится ко всем ссылкам, потомкам абзаца с классом first;
- ```p .first a {color: green;}``` — если добавить пробел, то будут стилизованы ссылки, расположенные внутри любого тега класса .first, который является потомком элемента \<p>;
- ```.first a {color: green;}``` — данный стиль применится к любой ссылке, расположенной внутри другого элемента, обозначенного классом .first.

### Дочерний селектор

Дочерний элемент является прямым потомком содержащего его элемента. У одного элемента может быть несколько дочерних элементов, а родительский элемент у каждого элемента может быть только один. Дочерний селектор позволяет применить стили только если дочерний элемент идёт сразу за родительским элементом и между ними нет других элементов, то есть дочерний элемент больше ни во что не вложен.

Например, ```p > strong``` — выберет все элементы strong, являющиеся дочерними по отношению к элементу p.

### Сестринский селектор
Сестринские отношения возникают между элементами, имеющими общего родителя. Селекторы сестринских элементов позволяют выбрать элементы из группы элементов одного уровня:

- ```h1 + p``` — выберет все первые абзацы, идущие непосредственно за любым тегом \<h1>, не затрагивая остальные абзацы;
- ```h1 ~ p``` — выберет все абзацы, являющиеся сестринскими по отношению к любому заголовку h1 и идущие сразу после него.

### Селектор атрибута
Селекторы атрибутов выбирают элементы на основе имени атрибута или значения атрибута:

- [атрибут] — все элементы, содержащие указанный атрибут, [alt] — все элементы, для которых задан атрибут alt;
- селектор[атрибут] — элементы данного типа, содержащие указанный атрибут, img[alt] — только картинки, для которых задан атрибут alt;
- селектор[атрибут="значение"] — элементы данного типа, содержащие указанный атрибут с конкретным значением, img[title="flower"] — все картинки, название которых содержит слово flower;

## Селектор псевдокласса

:focus — ссылки, а также элементы форм, которые активированы посредством курсора мыши или на которые перешли с помощью клавиатуры (кнопка TAB);

:hover — ссылки, а также другие элементы, стили применяются при наведении пользователем на элемент;

:active — выбирает элемент, активированный пользователем с помощью клика мышки. Обычно применяется для ссылок, но может отбирать и другие элементы на странице.

## Transition

CSS3-переходы позволяют анимировать исходное значение CSS-свойства на новое значение с течением времени, управляя скоростью смены значений свойств. Большинство свойств меняют свои значения за 16 миллисекунд, поэтому рекомендуемое время стандартного перехода — 200ms.

Смена свойств происходит при наступлении определенного события, которое описывается соответствующим псевдоклассом. Чаще всего используется псевдокласс :hover. Данный псевдокласс не работает на мобильных устройствах, таких как iPhone или Android. Универсальным решением, работающим в настольных и мобильных браузерах, будет обработка событий с помощью JavaScript (например, переключение классов при клике).

## Transform

CSS3-трансформации позволяют сдвигать, поворачивать и масштабировать элементы. Трансформации преобразовывают элемент, не затрагивая остальные элементы веб-страницы, т.е. другие элементы не сдвигаются относительно него.

К элементам, которые могут быть трансформированы, относятся элементы с display: block; и display: inline-block;, а также элементы, значение свойства display которых вычисляется как table-row, table-row-group, table-header-group, table-footer-group, table-cell или table-caption. Трансформированным считается элемент с любым установленным значением свойства transform, отличным от none.