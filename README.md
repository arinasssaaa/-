# Сравнение создания списков (массивов) и организации стеков в C++, Java и Python (Ширкина Арина УИБО-10-24)
## Создание списка (массива)
### C++
```cpp
#include <iostream>
#include <vector>

int main() {
    // Создание вектора (динамического массива)
    std::vector<std::string> fruits = {"яблоко", "банан", "апельсин"};
    std::vector<int> numbers = {1, 2, 3, 4, 5};
    
    // Добавление элементов
    fruits.push_back("киви");
    numbers.insert(numbers.begin(), 100);
    
    // Вывод элементов
    std::cout << "Фрукты: ";
    for (const auto& fruit : fruits) {
        std::cout << fruit << " ";
    }
    
    std::cout << "\nЧисла: ";
    for (int num : numbers) {
        std::cout << num << " ";
    }
    
    return 0;
}
```
· std::vector из STL как динамический массив
· Строгая типизация - все элементы одного типа
· Требуется указание типа данных
· Методы push_back() и insert() для добавления элементов
· Требуется ручной вывод элементов
· Высокая производительность, контроль над памятью

### Java
```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

public class ListExample {
    public static void main(String[] args) {
        // Создание списка (неизменяемого)
        List<String> fruits = Arrays.asList("яблоко", "банан", "апельсин");
        
        // Создание изменяемого списка
        List<String> mutableFruits = new ArrayList<>(fruits);
        List<Integer> numbers = new ArrayList<>(Arrays.asList(1, 2, 3, 4, 5));
        
        // Добавление элементов
        mutableFruits.add("киви");
        numbers.add(0, 100);
        
        System.out.println("Фрукты: " + mutableFruits);
        System.out.println("Числа: " + numbers);
    }
}
```
· ArrayList из Java Collections Framework
· Строгая типизация с дженериками
· Интерфейс List для абстракции реализации
· Методы add() для добавления элементов
· Автоматическое строковое представление
· Автоматическое управление памятью (JVM)

### Python
```py
# Создание списка
fruits = ['яблоко', 'банан', 'апельсин']
numbers = [1, 2, 3, 4, 5]

# Добавление элемента
fruits.append('киви')
numbers.insert(0, 100)

print("Фрукты:", fruits)  # ['яблоко', 'банан', 'апельсин', 'киви']
print("Числа:", numbers)  # [100, 1, 2, 3, 4, 5]
```
· Встроенный тип list как динамический массив
· Динамическая типизация - разные типы в одном списке
· Литералы квадратных скобок [] для создания
· Простой синтаксис добавления элементов (append(), insert())
· Автоматическое управление памятью

## Организация стеков
### C++
```cpp
#include <iostream>
#include <stack>

int main() {
    std::stack<int> myStack;
    
    // Добавление элементов в стек
    myStack.push(10);
    myStack.push(20);
    myStack.push(30);
    
    std::cout << "Размер стека: " << myStack.size() << std::endl;
    
    // Извлечение элементов
    std::cout << "Извлекаем элементы:" << std::endl;
    while (!myStack.empty()) {
        std::cout << myStack.top() << " ";  // Посмотреть вершину
        myStack.pop();  // Удалить вершину
    }
    
    return 0;
}
```
· std::stack из STL как адаптер контейнера
· Метод push() для добавления элементов
· Метод pop() для удаления элемента с вершины
· Метод top() для получения элемента без удаления
· Явная проверка пустоты (empty())
· Принцип LIFO (Last In, First Out)

### Java
```java
import java.util.Stack;

public class StackExample {
    public static void main(String[] args) {
        Stack<Integer> stack = new Stack<>();
        
        // Добавление элементов
        stack.push(10);
        stack.push(20);
        stack.push(30);
        
        System.out.println("Стек: " + stack);
        System.out.println("Вершина: " + stack.peek());
        
        // Извлечение элементов
        while (!stack.isEmpty()) {
            System.out.println("Извлекаем: " + stack.pop());
        }
    }
}
```
· Класс Stack из пакета java.util
· Метод push() для добавления элементов
· Метод pop() для извлечения и удаления
· Метод peek() для просмотра верхнего элемента
· Метод isEmpty() для проверки пустоты
· Наследует от Vector, потокобезопасен

### Python
```py
# Создание стека на основе списка
stack = []
stack.append(10)  # push
stack.append(20)
stack.append(30)

print("Стек:", stack)  # [10, 20, 30]

top = stack.pop()  # pop
print("Вершина:", top)  # 30
print("Стек после pop:", stack)  # [10, 20]
```
· Стек реализуется через стандартный список (list)
· Метод append() для добавления (push)
· Метод pop() для извлечения (pop)
· Простота использования, минимальный синтаксис

## Вывод

Каждый язык предлагает уникальный подход к работе со структурами данных:

· Python выделяется исключительной простотой синтаксиса и быстротой разработки, идеален для прототипирования и скриптов
· C++ предоставляет максимальный контроль над памятью и высочайшую производительность, оптимален для системного программирования
· Java сочетает строгую типизацию с богатой стандартной библиотекой, отлично подходит для кроссплатформенных enterprise-решений

Выбор языка зависит от конкретных требований проекта: необходимости в производительности (C++), простоте разработки (Python) или балансе между безопасностью и продуктивностью (Java).
