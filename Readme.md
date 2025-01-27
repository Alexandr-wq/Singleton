# Уникальные объекты #

## Вопросы и ответы

##### Маленькое упражнение в стиле сократовских диалогов

##### создание Одиночки
![kartinka1](https://github.com/Alexandr-wq/Singleton/blob/master/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA.PNG?raw=true)
![kartinka1](https://github.com/Alexandr-wq/Singleton/blob/master/2.PNG?raw=true)

#### Классическая реализация паттерна Одиночка

![kartinka1](https://github.com/Alexandr-wq/Singleton/blob/master/3.PNG?raw=true)

#### Шоколадная фабрика

##### Всем известно, что на всех современных шоколадных фабриках используются нагреватели с компьютерным управлением. Смесь шоколада и молока в таком нагревателе доводится до кипения и передается на следующий этап изготовления шоколадных батончиков. Ниже приведен код класса, управляющего ChocO-Holic — мощным высокопроизводительным нагревателем для шоколада. Просмотрите код; вы заметите, что автор постарался сделать все возможное, чтобы избежать некоторых неприятностей — скажем, слива холодной смеси, переполнения или нагревания пустой емкости!
![kartinka1](https://github.com/Alexandr-wq/Singleton/blob/master/4.PNG?raw=true)

##### нагреватель для шоколада. синглетная форма
##### Сможете ли вы усовершенствовать класс ChocolateBoiler,преобразовав его в синглетную форму (то есть с единственным экземпляром)?
![kartinka1](https://github.com/Alexandr-wq/Singleton/blob/master/5.PNG?raw=true)

## Определение паттерна Одиночка
#### Итак, вы познакомились с классической реализацией паттерна Одиночка. Сейчас можно устроиться поудобнее, съесть шоколадку и перейти к рассмотрению некоторых нюансов паттерна Одиночка.

##### Начнем с формального определения паттерна:
      ##### Паттерн Одиночка гарантирует, что класс имеет только один экземпляр, и предоставляет глобальную точку доступа к этому   экземпляру.
##### Пока ничего особенного. Но давайте присмотримся повнимательнее:
>Что здесь по сути происходит? Мы берем существующий класс и разрешаем ему создать только один экземпляр. Кроме того, мы запрещаем любым другим классам произвольно создавать новые экземпляры этого класса. Чтобы получить экземпляр, необходимо обратиться с запросом к самому классу.
>
>Кроме того, паттерн предоставляет глобальную точку доступа к экземпляру: обратившись с запросом к классу в любой точке программы, вы получите ссылку на
единственный экземпляр. Как было показано выше, возможно отложенное создание
экземпляра, что особенно важно для объектов, создание которых сопряжено с большими затратами ресурсов.

#### Обратимся к диаграмме классов:
![kartinka1](https://github.com/Alexandr-wq/Singleton/blob/master/6.PNG?raw=true)

### Кажется, у нас проблемы...
#### Похоже, программа управления нагревателем нас подвела; хотя мы усовершенствовали код и перешли на классическую реализацию паттерна Одиночка, метод fill() класса ChocolateBoiler почему-то начал заполнять емкость,которая уже была заполнена! 500 галлонов молока (и шоколада) пролилось на пол. Что произошло?!
#### Могло ли введение программных потоков привести к катастрофе? Ведь после того, как переменной uniqueInstance будет присвоен единственный экземпляр ChocolateBoiler, все вызовы getInstance() должны возвращать один и тот же экземпляр? Разве нет?
## Представьте, что вы — JVM...

### Есть два программных потока, в каждом из которых выполняется этот код.Ваша задача — представить себя в роли JVM и определить, не могут ли два потока в какой-то ситуации получить два разных объекта нагревателя. 
![kartinka1](https://github.com/Alexandr-wq/Singleton/blob/master/7.PNG?raw=true)
### Подсказка: проанализируйте последовательность операций в методе getInstance( ) и значение uniqueInstance, и подумайте, могут ли они перекрываться. Магниты с фрагментами кода помогут вам в поиске возможной последовательности действий, в результате которой программа может получить два объекта ChocolateBoiler.
![kartinka1](https://github.com/Alexandr-wq/Singleton/blob/master/8.PNG?raw=true)
## Решение проблемы многопоточного доступа
### Наши многопоточные проблемы решаются почти тривиально: метод getInstance() объявляется синхронизированным:
![kartinka1](https://github.com/Alexandr-wq/Singleton/blob/master/9.PNG?raw=true)
