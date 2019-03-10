# -- Черновик --
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
 
 # Строковые литералы
 
 В C/C++ и подобных для символов используется '', а для строк "". В интерпретируемых языках лучше использовать '' для строк, так как "" часто используется для вывода внутри строк, например HTML текста.
 
 Многострочные строки в C/C++ и подобынх языках обычно без проблем обрабатываются в "", так же возможна поддержка склейки строк. В Python для многострочных строк лучше использовать ''', так как """ может использоваться внутри. Так же в Python необходимо по максимому использовать строки без обработки внутренних символов предварённые символом r. В некторых языках нет многострочных строк и тогда приходится использовать '\n' внутри, а иногда это невозможно. Для таких сулчаев лучше использовать сложение строк без присваивания.
 
 # Комментарии
 
 Язык комментариев только английский!
 
 В C-подобных языках принято использовать '/\/' для однострочных комментариев и '/\*\*/' для многострочных, а '#' зарезервирован под препроцессор. В других может использоваться один вид комментариев, например как '/\*\*/' в CSS для любых комментариев или как # в Python для однострочных комментариев. В скриптовых языках возможно использовать не присвоенные строковые литералы для многострочных комментариев, например как в Python, но это может увеличивать нагрузку на парсер, так как не игнарируются во время парсинга, так что лучше использовать так же однострочные комментарии для каждой строки. Так же парсинг однострочных комментариев типа '#' и '/\/' быстрее, чем конструкций типа '/**/', поэтому по возможности лучше использовать однострочные комментарии.
 
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

# Ключевые слова и зарезервированные слова

and
abstract', ['keyword', 'modifer']),
arguments', ['keyword', 'pseudo']),
await', ['keyword', 'modifer']),
async', ['keyword', 'modifer']),
array', ['keyword', 'type']),
assert', ['keyword', 'function']),
and_eq', ['keyword', 'operator']),
as', ['keyword', 'operator']),
asm', ['keyword', 'block']),
auto', ['keyword', 'type']),
bitand', ['keyword', 'operator']),
	new Token('bitor', ['keyword', 'operator']),
	new Token('bool', ['keyword', 'type']),
	new Token('boolean', ['keyword', 'type']),
	new Token('break', ['keyword', 'function']),
	new Token('byte', ['keyword', 'type']),
	new Token('case', ['keyword', 'block']),
	new Token('catch', ['keyword', 'block']),
	new Token('char', ['keyword', 'type']),
	new Token('checked', ['keyword', 'block']),
	new Token('class', ['keyword', 'block']),
	new Token('clone', ['keyword', 'function']),
	new Token('compl', ['keyword', 'operator']),
	new Token('const', ['keyword', 'modifer']),
	new Token('const_cast', ['keyword', 'function']),
	new Token('continue', ['keyword', 'function']),
	new Token('callable', ['keyword', 'type']),
	new Token('debugger', ['keyword', 'function']),
	new Token('default', ['keyword', 'block']),
	new Token('declare', ['keyword', 'block']),
	new Token('decimal', ['keyword', 'type']),
	new Token('die', ['keyword', 'function']),
	new Token('def', ['keyword', 'modifer']),
	new Token('delete', ['keyword', 'function']),
	new Token('del', ['keyword', 'function']),
	new Token('do', ['keyword', 'block']),
	new Token('double', ['keyword', 'type']),
	new Token('dynamic_cast', ['keyword', 'function']),
	new Token('else', ['keyword', 'block']),
	new Token('elseif', ['keyword', 'block']),
	new Token('elif', ['keyword', 'block']),
	new Token('enum', ['keyword', 'block']),
	new Token('except', ['keyword', 'block']),
	new Token('echo', ['keyword', 'function']),
	new Token('empty', ['keyword', 'function']),
	new Token('enddeclare', ['keyword', 'function']),
	new Token('endfor', ['keyword', 'function']),
	new Token('endforeach', ['keyword', 'function']),
	new Token('endif', ['keyword', 'function']),
	new Token('endswitch', ['keyword', 'function']),
	new Token('endwhile', ['keyword', 'function']),
	new Token('eval', ['keyword', 'function']),
	new Token('exit', ['keyword', 'function']),
	new Token('explicit', ['keyword', 'modifer']),
	new Token('export', ['keyword', 'block']),
	new Token('extern', ['keyword', 'block']),
	new Token('extends', ['keyword', 'operator']),
	new Token('exec', ['keyword', 'function']),
	new Token('event', ['keyword', 'modifer']),
	new Token('false', ['keyword', 'value']),
	new Token('final', ['keyword', 'modifer']),
	new Token('finally', ['keyword', 'modifer']),
	new Token('float', ['keyword', 'type']),
	new Token('for', ['keyword', 'block']),
	new Token('from', ['keyword', 'operator']),
	new Token('foreach', ['keyword', 'block']),
	new Token('function', ['keyword', 'modifer']),
	new Token('friend', ['keyword', 'modifer']),
	new Token('fixed', ['keyword', 'modifer']),
	new Token('goto', ['keyword', 'function']),
	new Token('global', ['keyword', 'modifer']),
	new Token('get', ['keyword', 'block']),
	new Token('if', ['keyword', 'block']),
	new Token('ifn', ['keyword', 'block']),
	new Token('implements', ['keyword', 'operator']),
	new Token('implicit', ['keyword', 'modifer']),
	new Token('import', ['keyword', 'function']),
	new Token('include', ['keyword', 'function']),
	new Token('include_once', ['keyword', 'function']),
	new Token('in', ['keyword', 'operator']),
	new Token('instanceof', ['keyword', 'operator']),
	new Token('insteadof', ['keyword', 'operator']),
	new Token('inline', ['keyword', 'modifer']),
	new Token('internal', ['keyword', 'modifer']),
	new Token('int', ['keyword', 'type']),
	new Token('interface', ['keyword', 'block']),
	new Token('isset', ['keyword', 'function']),
	new Token('is', ['keyword', 'operator']),
	new Token('lambda', ['keyword', 'function']),
	new Token('let', ['keyword', 'type']),
	new Token('long', ['keyword', 'modifer']),
	new Token('list', ['keyword', 'type']),
	new Token('lock', ['keyword', 'block']),
	new Token('mutable', ['keyword', 'modifer']),
	new Token('namespace', ['keyword', 'block']),
	new Token('native', ['keyword', 'modifer']),
	new Token('null', ['keyword', 'value']),
	new Token('new', ['keyword', 'function']),
	new Token('not', ['keyword', 'operator']),
	new Token('not_eq', ['keyword', 'operator']),
	new Token('operator', ['keyword', 'modifer']),
	new Token('or', ['keyword', 'operator']),
	new Token('or_eq', ['keyword', 'operator']),
	new Token('object', ['keyword', 'type']),
	new Token('out', ['keyword', 'modifer']),
	new Token('override', ['keyword', 'modifer']),
	new Token('package', ['keyword', 'function']),
	new Token('params', ['keyword', 'modifer']),
	new Token('private', ['keyword', 'modifer']),
	new Token('protected', ['keyword', 'modifer']),
	new Token('public', ['keyword', 'modifer']),
	new Token('print', ['keyword', 'function']),
	new Token('pass', ['keyword', 'function']),
	new Token('readonly', ['keyword', 'modifer']),
	new Token('register', ['keyword', 'function']),
	new Token('ref', ['keyword', 'modifer']),
	new Token('reinterpret_cast', ['keyword', 'function']),
	new Token('return', ['keyword', 'function']),
	new Token('require', ['keyword', 'function']),
	new Token('require_once', ['keyword', 'function']),
	new Token('raise', ['keyword', 'function']),
	new Token('sbyte', ['keyword', 'type']),
	new Token('short', ['keyword', 'modifer']),
	new Token('sealed', ['keyword', 'modifer']),
	new Token('signed', ['keyword', 'modifer']),
	new Token('sizeof', ['keyword', 'function']),
	new Token('super', ['keyword', 'function']),
	new Token('static', ['keyword', 'modifer']),
	new Token('stackalloc', ['keyword', 'function']),
	new Token('static_cast', ['keyword', 'function']),
	new Token('string', ['keyword', 'type']),
	new Token('str', ['keyword', 'type']),
	new Token('struct', ['keyword', 'block']),
	new Token('switch', ['keyword', 'block']),
	new Token('synchronized', ['keyword', 'modifer']),
	new Token('sync', ['keyword', 'modifer']),
	new Token('self', ['keyword', 'pseudo']),
	new Token('set', ['keyword', 'block']),
	new Token('template', ['keyword', 'modifer']),
	new Token('this', ['keyword', 'pseudo']),
	new Token('throw', ['keyword', 'function']),
	new Token('throws', ['keyword', 'modifer']),
	new Token('transient', ['keyword', 'modifer']),
	new Token('true', ['keyword', 'value']),
	new Token('try', ['keyword', 'block']),
	new Token('trait', ['keyword', 'block']),
	new Token('typedef', ['keyword', 'function']),
	new Token('typeid', ['keyword', 'function']),
	new Token('typename', ['keyword', 'function']),
	new Token('typeof', ['keyword', 'function']),
	new Token('union', ['keyword', 'block']),
	new Token('uint', ['keyword', 'type']),
	new Token('unsigned', ['keyword', 'modifer']),
	new Token('using', ['keyword', 'function']),
	new Token('ulong', ['keyword', 'type']),
	new Token('ushort', ['keyword', 'type']),
	new Token('unset', ['keyword', 'function']),
	new Token('use', ['keyword', 'operator']),
	new Token('unchecked', ['keyword', 'block']),
	new Token('unsafe', ['keyword', 'modifer']),
	new Token('virtual', ['keyword', 'modifer']),
	new Token('void', ['keyword', 'type']),
	new Token('var', ['keyword', 'type']),
	new Token('volatile', ['keyword', 'modifer']),
	new Token('wchar_t', ['keyword', 'type']),
	new Token('while', ['keyword', 'block']),
	new Token('with', ['keyword', 'block']),
	new Token('where', ['keyword', 'operator']),
	new Token('xor', ['keyword', 'operator']),
	new Token('xor_eq', ['keyword', 'operator']),
    new Token('yield', ['keyword', 'function'])];
