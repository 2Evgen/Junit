# Домашнее задание к занятию «Система сборки Maven, управление зависимостями, автотесты на JUnit5»

##  Инструкция к выполнению домашнего задания

Перед тем как отправить своё решение на проверку преподавателю, сверьтесь с чеклистом.

<details>
  <summary> 1. В решении выполнены все требования задания</summary>
  
  Убедитесь, что все требования задания выполнены. Для этого перед отправкой внимательно прочтите весь текст условия задания и соотнесите сказанное в нём с вашим решением. Навык самопроверки работы перед ревью пригодится вам как при обучении, так и на работе.

  ---
  
</details>
<details open>
  <summary>2. Правильно настроен Maven-проект, тесты проходят :new:</summary>
  
  Репозиторий должен быть папкой вашего Мавен-проекта. Обратите внимание, что репозиторием не должна быть папка, в которой лежит папка Мавен-проекта, он сам должен быть папкой проекта. В нём должны быть соответствующие файлы и папки — `pom.xml`, `src` и другие.
  
  Не забудьте создать .gitignore-файл в корне проекта и добавить туда в игнорирование автогенерируемую папку `target`.
  
  Общая схема вашего `pom.xml`-файла:
  
  ```xml
  <?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>ru.netology</groupId>
    <artifactId>НАЗВАНИЕ-ВАШЕГО-ПРОЕКТА-БЕЗ-ПРОБЕЛОВ</artifactId>
    <version>1.0-SNAPSHOT</version>

    <properties>
        <maven.compiler.source>11</maven.compiler.source>
        <maven.compiler.target>11</maven.compiler.target>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    </properties>


    <dependencies>
        <dependency>
            ...
        </dependency>
        ...
    </dependencies>


    <build>
        <plugins>
            <plugin>
              ...
            </plugin>

            <plugin>
              ...
              <executions>
                <execution>
                  ...
                </execution>
                ...
              </executions>
            </plugin>
            ...
        </plugins>
    </build>

</project>
  ```
  
  #### JUnit
  Обратите внимание, что у артефакта нет `-api` на конце. Если у вас автоматически добавилась зависимость вида `<artifactId>junit-jupiter-api</artifactId>`, то лучше поменять артефакт на тот, что ниже, иначе будут сюрпризы в работе.

  ```xml
          <dependency>
              <groupId>org.junit.jupiter</groupId>
              <artifactId>junit-jupiter</artifactId>
              <version>5.7.0</version>
              <scope>test</scope>
          </dependency>
  ```

  #### Surefire
  Без этого плагина тесты могут Мавеном не запускаться, хоть в идее через кнопки они и будут проходить. Чтобы лишний раз убедиться, что всё работает, нажмите `Ctrl+Ctrl` и затем `mvn clean test`.
  
  ```xml
              <plugin>
                  <groupId>org.apache.maven.plugins</groupId>
                  <artifactId>maven-surefire-plugin</artifactId>
                  <version>2.22.2</version>
                  <configuration>
                      <failIfNoTests>true</failIfNoTests>
                  </configuration>
              </plugin>
  ```
  
  ---
  
</details>

<details>
   <summary> 3. Что делать, если возникли сложности </summary>
  
Это здорово. Если их преодолевать правильно, то можно получить большую образовательную пользу для себя. Периодическое возникновение вопросов, недопонимание пройденного материала — нормальная и неотъемлемая часть обучения. А мы здесь, чтобы помочь вам пройти этот путь.
  
  ### Что делать, если непонятна теория
  1. Если подобный вопрос разбирался на лекции, посмотрите ещё раз раздел с этой темой в видеозаписи.
  1. Если вопрос не решился, попробуйте поискать ответ самостоятельно в интернете, этот навык пригодится вам в работе.
  1. Если самостоятельно разобраться не удалось, задайте вопрос в общем чате, мы обязательно поможем.

  ### Что делать, если непонятно условие задания
  1. Прежде чем задать вопрос по условию задачи, перечитайте его ещё раз и убедитесь, что в тексте условия нет прямого ответа на этот вопрос. Умение работать с текстом — важный навык работы с информацией.
  1. Если ответа на свой вопрос в тексте условия не увидели, задайте его в общем чате, мы раскроем детали условия.

  ### Что делать, если не получается задача
Если ваша проблема — это **ошибка компиляции** — подчёркивает красным, не даёт запустить программу, сборки проекта, CI и прочие подобные ошибки, то:
  1. Найдите и прочитайте текст ошибки, который вам подсвечивает идея или логи. «Подчёркивает красным» — это не описание ошибки.
  1. Попробуйте понять текст ошибки, при необходимости воспользуйтесь переводчиком. Не страшно, если вы переведёте неточно, тут главное — сам процесс: со временем и с нашей помощью вы будете это делать лучше и лучше, но, пропуская этот этап, вы не сможете научиться это делать.
  1. Если не получилось понять ошибку по её тексту, попробуйте её загуглить и изучить подобную ошибку у других людей. Попробуйте примерить решения их проблем на свой код. Соотнесите найденные описания ошибки с пройденной теорией.
  1. Если всё равно ваши трудности не разрешились, напишите в общий чат, обязательно указав:
      1. название задачи и ссылку на условие;
      1. ссылку на вашу работу;
      1. текст и скриншот, не фотографию, ошибки;
      1. ваши размышления и описание шагов, которые вы совершили для решения.

Если ваша проблема — это **ошибка исполнения**, программа умирает уже после запуска, или она **отрабатывает неправильно**, из-за чего ваши тесты не проходят, то:
  1. Воспользуйтесь отладчиком для пошагового анализа работы вашей программы. Так вы или убедитесь в неправильности придуманного вами алгоритма, или найдёте конкретное место, где ожидаемое поведение программы разошлось с фактическим.
  1. Если проблему найти не получилось, напишите в общий чат, обязательно указав:
      1. название задачи и ссылку на условие;
      1. ссылку на вашу работу;
      1. конкретное и подробное описание проблемы или затруднения при решении задачи. «Помогите, что-то не так» — это не описание;
      1. подробное описание вашего анализа программы с помощью отладчика вместе со скринами;
      1. ваши размышления и описание шагов, которые вы совершили для решения.
  ---
  
</details>
  

<details open>
  <summary>4. Отформатирован код</summary>
  
Кроме правил, нарушение которых приводит к ошибкам компиляции, есть ещё и [правила форматирования кода](https://google.github.io/styleguide/javaguide.html), соблюдение которых обязательно при написании программ.
  
С большинством проблем может справиться автоформатирование в идее. Для этого выберите `Code -> Reformat code` в меню или используйте горячие сочетания клавиш. В меню будет показано актуальное сочетание для вашей операционной системы. Так, идея поправит неправильные отступы, пробелы и некоторые другие ошибки. Следите, чтобы у `if-else`, `for`, `while` всегда были `{}`.
  
  Проблемы с именованием сущностей нужно решать самим. Так, все ячейки, кроме `final`-констант, и методы должны писаться [камелкейсом](https://ru.wikipedia.org/wiki/CamelCase) с **маленькой** буквы, а классы и интерфейсы — камелкейсом с **большой** буквы.
  
  Мы вам настоятельно советуем всегда держать код в отформатированном виде во время разработки, со временем глаз привыкнет, и вы почувствуете, насколько это облегчает поиск ошибок в коде и его анализ. В любом случае перед отправкой кода на проверку его обязательно нужно отформатировать, иначе он может быть отправлен на доработку без более глубокой проверки на этой итерации.
</details>

# Задание 1. Дописываем тесты (обязательное к выполнению)
Нашей целью будет переделать проект с приложением про бонус с покупки на Мавен и хорошо его протестировать.

**Шаг 1.** Создайте проект на базе Maven.

**Шаг 2.** Добавьте в проект JUnit Jupiter & Surefire Plugin

**Шаг 3.** Создайте сервисный класс со следующим исходным кодом:
```java
public class BonusService {
  public long calculate(long amount, boolean registered) {
    int percent = registered ? 3 : 1;
    long bonus = amount * percent / 100;
    long limit = 500;
    if (bonus > limit) {
      bonus = limit;
    }
    return bonus;
  }
}
```

**Шаг 4.** Создайте тестовый класс со следующим исходным кодом:
```java
import static org.junit.jupiter.api.Assertions.*;

public class BonusServiceTest {

  @org.junit.jupiter.api.Test
  void shouldCalculateForRegisteredAndUnderLimit() {
    BonusService service = new BonusService();

    // подготавливаем данные:
    long amount = 1000;
    boolean registered = true;
    long expected = 30;

    // вызываем целевой метод:
    long actual = service.calculate(amount, registered);

    // производим проверку (сравниваем ожидаемый и фактический):
    assertEquals(expected, actual);
  }

  @org.junit.jupiter.api.Test
  void shouldCalculateForRegisteredAndOverLimit() {
    BonusService service = new BonusService();

    // подготавливаем данные:
    long amount = 1_000_000;
    boolean registered = true;
    long expected = 500;

    // вызываем целевой метод:
    long actual = service.calculate(amount, registered);

    // производим проверку (сравниваем ожидаемый и фактический):
    assertEquals(expected, actual);
  }
}
```

**Шаг 5.** Запустите тесты через `mvn clean test`, убедитесь, что они запускаются и проходят.

**Шаг 6.** Проведите тест-дизайн сервисного класса, очень глубоко его можно не проводить, допишите недостающие тесты.

**Шаг 7.** Убедитесь, что тесты запускаются и проходят.

Итого: отправьте на проверку ссылку на репозиторий GitHub с вашим проектом.

# Задание 2. Читаем логи (необязательная задача повышенной сложности)

Ваш коллега — очень любознательный товарищ. Узнав про то, что Maven может использовать плагины, он сразу начал искать, какие плагины есть.

И нашёл один, с его точки зрения, достаточно замечательный плагин, который ищет ошибки в коде.

Представляете? Сам ищет ошибки в коде!

Естественно, он не преминул этим воспользоваться, загуглил, как подключить этот плагин и даже смог его запустить на одном из наших проектов.

Но поскольку он не совсем разобрался, как работать с логами, он не совсем понимает, что и где не так и куда смотреть.

Поэтому он обратился к вам.

Ваша задача:
1. Взять проект, который прикреплён в архиве [`bonus-service.zip`](https://github.com/netology-code/javaqa2-homeworks/blob/main/files/bonus-service.zip?raw=true).
1. Открыть его как Maven проект в IDEA.
1. Запустить следующую команду Maven*: `mvn clean compile spotbugs:check`. Ваш коллега не может объяснить, что это значит, но говорит, что запускать нужно именно так.
1. Проанализировать логи, выяснить в чём ошибка. Воспользуйтесь гуглом по типу ошибки и чтением документации.
1. Исправить ошибку так, чтобы повторный вызов `mvn clean compile spotbugs:check` завершался успешно, менять `pom.xml` нельзя.

Как выкладывать проект на GitHub:
1. Заливаете исходную версию.
1. Создаёте issue* с описанием того, что не так, и прикладываете кусок лога, из которого это видно, плюс ссылку на проблемный участок кода.
1. Фиксите всё с сообщением коммита `fixed #1`, где 1 — это id issue.
1. Заливаете на GitHub, удостоверяетесь, что после пуша issue автоматически закроется.

Примечание*: как работать с issue, описано в третьей лекции курса по Git и в первом домашнем задании блока по Java.

### Результат
При отправке решения в личном кабинете прикрепите ссылку на ваш публичный репозиторий GitHub с вашим проектом.
