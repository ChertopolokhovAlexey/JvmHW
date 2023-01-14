public class JvmComprehension {

    public static void main(String[] args) {
        int i = 1;                      // 1
        Object o = new Object();        // 2
        Integer ii = 2;                 // 3
        printAll(o, i, ii);             // 4
        System.out.println("finished"); // 7
    }

    private static void printAll(Object o, int i, Integer ii) {
        Integer uselessVar = 700;                   // 5
        System.out.println(o.toString() + i + ii);  // 6
    }
}

### Описание работы кода
ClassLoader загружает класс "JvmComprehension."
Метод "main"  создает frame в StackMemory
1. В "main frame" заносится переменная "i" примитивного типа int и ему присваивается значение "1".
2. Создается новый объект "Object". Под него резервируется место в heap. В "main frame" создается ссылка на него "o".
3. Создается переменная "ii" ссылочного типа "Integer". Под неё резервируется место в heap. В "main frame" создается ссылка на него "ii=2".
4. Запускается метод "printAll".
Метод "printAll" создает frame в StackMemory. Принимает ссылку на "o",""ii" и переменную "i" как входные параметры
5. Создается переменная "uselessVar" ссылочного типа "Integer". Под нё резервируется место в heap. В "printAll frame" создается ссылка на него "uselessVar=700".
6. Запуск метода вывода в консоль "sout".
Метод "sout" создает frame в StackMemory. Принимает ссылку на "o",""ii" и переменную "i" как входные параметры.
Выводит в консоль "Object" в соответствии с методом toString(), сращивая со значениями "i" и "ii"
Метод "sout" завершен. Закрытие его фрейма.
Метод "printAll" закончен. Из heap удаляется переменная "uselessVar". Закрытие его фрейма.
7. Запуск метода вывода в консоль "sout".
Метод "sout" создает frame в StackMemory. Создается ссылочная переменная типа String в heap. Заносится текстовое значение. В текущем frame сохраняется ссылка на нее.
После вывода в консоль метод "sout" завершен. Из heap удаляется переменная типа String. Закрытие его фрейма.
Завершение метода "main". "Heap" очищается. Закрытие его фрейма.

