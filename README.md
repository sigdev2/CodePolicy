# CodePolicy

Цель данного документа стандартизировать стили и подходы к программированию с сочетание синтаксиса и конструкций моножества языков в одном кодовом простаранстве или одном документе. Поэтому описание будет самое общее и на примере конкретных языков. Остальные языки подгоняются по возможно по подходящим примерам.

# Оглавление

 - Используемые символы
 - Строковые литералы
 - Комментарии
 - Ключевые слова и зарезервированные слова
 - Блоки кода
 - Конструкции языка
 - Правила именования, употребялемые слова
 - Простые типы
 - Контейнерные типы
 - Операции над типами
 - Описания структур
   - XML/HTML
   - JSON
 
 # Используемые символы
 
 Для кода можно использовать 'A-z0-9', '()[]{}<>.,:;!?-=+_*&^%$#@~`'"/\|'. В строковых литералах и комментариях любые другие символы. Символы могут быть экранированы при помощи '\'.
 
 Так же используются пробельные симыолы '\n', '\t' и пробел. При этом '\n' используется для перевода строк. (Даже под Windows вместо '\r\n').
 
 Длинна строк не должна превышать 78 символов.
 
 # Стрококвые литералы
 
 В C/C++ и подобных для символов используется '', а для строк "". В интерпретируемых языках лучше использовать '' для строк, так как "" часто используется для вывода внутри строк, например HTML текста.
 
 Многострочные строки в C/C++ и подобынх языках обычно без проблем обрабатываются в "", так же возможна поддержка склейки строк. В Python для многострочных строк лучше использовать ''', так как """ может использоваться внутри. Так же в Python необходимо по максимому использовать строки без обработки внутренних символов предварённые символом r. В некторых языках нет многострочных строк и тогда приходится использовать '\n' внутри, а иногда это невозможно. Для таких сулчаев лучше использовать сложение строк без присваивания.
 
 # Комментарии
 
 В C-подобных языках принято использовать '/\/' для однострочных комментариев и '/\*\*/' для многострочных, а '#' зарезервирован под препроцессор. В других может использоваться один вид комментариев, например как '/\*\*/' в CSS для любых комментариев или как # в Python для однострочных комментариев. В скриптовых языках возможно использовать не присвоенные строковые литералы для многострочных комментариев, например как в Pythin, но это может увеличивать нагрузку на парсер, так как не игнарируются во время парсинга, так что лучше использовать так же однострочные комментарии для каждой строки. Так же парсинг однострочных комментариев типа '#' и '/\/' быстрее, чем конструкций типа '/**/', поэтому по возможности лучше использовать однострочные комментарии.
 
 Знаки начала и конца комментария лучше отделять пробелом: '/\/ 123', '/* 123 */'
 
Для чёткого понимания отношения комментария к конкретному куску кода лучше придерживаться следуюбщих правил:
  - Короткий комментарий к строке можно расположить в конце строки за два пробела от последнего символа:

    same code  # comment
 
  - Длинный комментарий стоит распологать строкой выше комментируемой строки, начиная её на том же уровне:

    \# comment      
    some code
  
   - Свободный коментарий начинается на уровне блока, а снизу отрезается пустой строкой. Такой комментарий относится ко всему блоку или документу, в котором он распологается. Не стоит распологать такие комментарии в середине блока, лучше откомментировать конкретные строки.
   
   - Отдельно упоминается вид свободных комментариев, как ограничитель блока кода. Он отсекается пустой строкой сверху, кроме того случая когда это первая стока в блоке или документе. Снизу же кроме пустой строки он отсекается 8-ю символами начала однострочного комментария:
   
    # part 1  
    ########
    
    // part 2  
    ////////////////

Коментарий может начинаться со специального слова-метки, которые пишуться заглавными буквами и оканчиваются ':' с пробелом. Например:

    # NOTE: same note

Список устоявшихся меток:
 - NOTE: заметка
 - TODO: для доработок
 - WARN: опасность
 - FIXME: к правке
 - BUG: ошибка
 - HACK: хак, который лучше бы переписать
 - OPTIMIZE: необходима оптимизация
