# Пошаговое описание того, что происходит в JVM при работе программы


###1-ый этап(ClassLoaders):
* Обращаемся к подсиситеме загрузчиков классов Class Loading, чтобы она подгрузила наш класс JvmComprehension.
Подсистема состоит из трёх загрузчиков: Application ClassLoader, Platform ClassLoader, Bootstrap ClassLoader (от врехнего уровня до нижнего, в порядке в котором указаны). Application ClassLoader передаёт запрос по цепочке Platform ClassLoader, спрашивая у него "Есть ли такие классы?". Platform ClassLoader в свою очередь также делегирует запрос к Bootstrap ClassLoader, спрашивая у него "Может ли он загрузить эти классы?". Bootstrap ClassLoader пробует загрузить эти классы, если получается, то работа подсистемы заканчивается, класс загружен. Если у него это не получается, то он по обратной цепочке передаёт об этом информацию Platform ClassLoader. Теперь Platform ClassLoader ищет наш класс, если находит, то подгружает, если не находит, то он передаёт об этом информацию Application ClassLoader. Application ClassLoader начинает искать наш класс сам. Если такой класс есть, то он его подгружает, если нет, то будет ошибка ClassNotFoundException. Наш класс,JvmComprehension, будет найден и загруже.
*Далее происходит *связывание(Linking)*. 
