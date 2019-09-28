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
