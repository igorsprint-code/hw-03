### Задание 1
Создайте свой шаблон, в котором будут элементы данных, мониторящие загрузку CPU и RAM хоста.

#### Процесс выполнения
1. Выполняя ДЗ сверяйтесь с процессом отражённым в записи лекции.
2. В веб-интерфейсе Zabbix Servera в разделе Templates создайте новый шаблон
3. Создайте Item который будет собирать информацию об загрузке CPU в процентах
4. Создайте Item который будет собирать информацию об загрузке RAM в процентах

#### Требования к результату
- [ ] Прикрепите в файл README.md скриншот страницы шаблона с названием «Задание 1»

### Решение
Создан новый шаблон "Zadanie 1" с двумя item, которые  будет собирать информацию об загрузке CPU и RAM в процентах:

![screen](https://github.com/igorsprint-code/hw-03/blob/main/Zadanie1.jpg)

 ---

### Задание 2
Добавьте в Zabbix два хоста и задайте им имена <фамилия и инициалы-1> и <фамилия и инициалы-2>. Например: ivanovii-1 и ivanovii-2.

#### Процесс выполнения
1. Выполняя ДЗ сверяйтесь с процессом отражённым в записи лекции.
2. Установите Zabbix Agent на 2 виртмашины, одной из них может быть ваш Zabbix Server
3. Добавьте Zabbix Server в список разрешенных серверов ваших Zabbix Agentов
4. Добавьте Zabbix Agentов в раздел Configuration > Hosts вашего Zabbix Servera
5. Прикрепите за каждым хостом шаблон Linux by Zabbix Agent
6. Проверьте что в разделе Latest Data начали появляться данные с добавленных агентов

#### Требования к результату
- [ ] Результат данного задания сдавайте вместе с заданием 3

### Решение

Решение в задании №3

 ---

### Задание 3
Привяжите созданный шаблон к двум хостам. Также привяжите к обоим хостам шаблон Linux by Zabbix Agent.

#### Процесс выполнения
1. Выполняя ДЗ сверяйтесь с процессом отражённым в записи лекции.
2. Зайдите в настройки каждого хоста и в разделе Templates прикрепите к этому хосту ваш шаблон
3. Так же к каждому хосту привяжите шаблон Linux by Zabbix Agent
4. Проверьте что в раздел Latest Data начали поступать необходимые данные из вашего шаблона

#### Требования к результату
- [ ] Прикрепите в файл README.md скриншот страницы хостов, где будут видны привязки шаблонов с названиями «Задание 2-3». Хосты должны иметь зелёный статус подключения

### Решение

К каждому хосту приклеплен шаблон Zadanie 1

Первый хост:

![screen](https://github.com/igorsprint-code/hw-03/blob/main/temp%201.jpg)

Второй хост:

![screen](https://github.com/igorsprint-code/hw-03/blob/main/temp%202.jpg)
 
Привяжите шаблон Linux by Zabbix Agent нельзя т.к. в оба шаблона содержат одинаковый item system.cpu.util

![screen](https://github.com/igorsprint-code/hw-03/blob/main/linux%20by%20zabbix.jpg)

В раздел Latest Data начали поступать необходимые данные из шаблона


![screen](https://github.com/igorsprint-code/hw-03/blob/main/latest_data.jpg)

 ---

### Задание 4
Создайте свой кастомный дашборд.

#### Процесс выполнения
1. Выполняя ДЗ сверяйтесь с процессом отражённым в записи лекции.
2. В разделе Dashboards создайте новый дашборд
3. Разместите на нём несколько графиков на ваше усмотрение.

#### Требования к результату
- [ ] Прикрепите в файл README.md скриншот дашборда с названием «Задание 4»

### Решение

Новый дашборд:

![screen](https://github.com/igorsprint-code/hw-03/blob/main/dash.jpg)


 ---

### Задание 5* со звёздочкой
Создайте карту и расположите на ней два своих хоста.

#### Процесс выполнения
1. Настройте между хостами линк.
2. Привяжите к линку триггер, связанный с agent.ping одного из хостов, и установите индикатором сработавшего триггера красную пунктирную линию.
3. Выключите хост, чей триггер добавлен в линк. Дождитесь срабатывания триггера.

#### Требования к результату
- [ ] Прикрепите в файл README.md скриншот карты, где видно, что триггер сработал, с названием «Задание 5»

### Решение

Настроенный линк и триггер между хостами:

![screen](https://github.com/igorsprint-code/hw-03/blob/main/trigger%20on%20map.jpg)

Выключение хоста:

![screen](https://github.com/igorsprint-code/hw-03/blob/main/cloud%20stop.jpg)

Срабатывание триггера:

![screen](https://github.com/igorsprint-code/hw-03/blob/main/stop%20on%20map.jpg)



 ---

### Задание 6* со звёздочкой
Создайте UserParameter на bash и прикрепите его к созданному вами ранее шаблону. Он должен вызывать скрипт, который:
- при получении 1 будет возвращать ваши ФИО,
- при получении 2 будет возвращать текущую дату.

#### Требования к результату
- [ ] Прикрепите в файл README.md код скрипта, а также скриншот Latest data с результатом работы скрипта на bash, чтобы был виден результат работы скрипта при отправке в него 1 и 2

Скрипт:

```bash
#!/bin/bash
PARAM=$1

if [ "$PARAM" == "1" ]; then
        echo "Dedyakhin I.V."

elif [ "$PARAM" == "2" ]; then
        echo "$(date '+%d.%m.%Y %H:%M:%S')"
else
        echo "ERROR. Use parameter 1 or 2 " 

fi


```

Содержание файла user_parameter.conf:

```
UserParameter=custom_FIO[*],./etc/zabbix/zabbix_agentd.d/user_parameter.sh 1
UserParameter=custom_date[*],./etc/zabbix/zabbix_agentd.d/user_parameter.sh 2
```

Добавляем пользовательские items в наш шаблон:

![screen](https://github.com/igorsprint-code/hw-03/blob/main/bash_temp.jpg)


Latest data с результатом работы скрипта на bash:

![screen](https://github.com/igorsprint-code/hw-03/blob/main/bash_data.jpg)

 
 ---

### Задание 7* со звёздочкой
Доработайте Python-скрипт из лекции, создайте для него UserParameter и прикрепите его к созданному вами ранее шаблону. 
Скрипт должен:
- при получении 1 возвращать ваши ФИО,
- при получении 2 возвращать текущую дату,
- делать всё, что делал скрипт из лекции.

- [ ] Прикрепите в файл README.md код скрипта в Git. Приложите в Git скриншот Latest data с результатом работы скрипта на Python, чтобы были видны результаты работы скрипта при отправке в него 1, 2, -ping, а также -simple_print.*

Код скрипта:
```python
import sys
import os
import re
import datetime

if (sys.argv[1] == '-ping'): # Если -ping
        result=os.popen("ping -c 1 " + sys.argv[2]).read() # Делаем пинг по заданному адресу
        result=re.findall(r"time=(.*) ms", result) # Выдёргиваем из результата время
        print(result[0]) # Выводим результат в консоль
elif (sys.argv[1] == '-simple_print'): # Если simple_print
        print(sys.argv[2]) # Выводим в консоль содержимое sys.arvg[2]
elif (sys.argv[1] == '1'):
        print(f"Dedyakhin I.V.")
elif (sys.argv[1] == '2'):
        print(datetime.datetime.now())

else: # Во всех остальных случаях
        print(f"unknown input: {sys.argv[1]}") # Выводим непонятый запрос в консоль

```

Файл user_parameter.conf:
```
UserParameter=custom_py_FIO[*],python3 /etc/zabbix/zabbix_agentd.d/test_python_script.py 1
UserParameter=custom_py_date[*],python3 /etc/zabbix/zabbix_agentd.d/test_python_script.py 2
UserParameter=custom_py_ping[*],python3 /etc/zabbix/zabbix_agentd.d/test_python_script.py -ping 8.8.8.8
UserParameter=custom_py_print[*],python3 /etc/zabbix/zabbix_agentd.d/test_python_script.py -simple_print test

```

Добавляем в шаблон item'ы:

![screen](https://github.com/igorsprint-code/hw-03/blob/main/888_1_temp.jpg)

Latest data с результатом работы скрипта на python:

![screen](https://github.com/igorsprint-code/hw-03/blob/main/888__data.jpg)



 
 ---

### Задание 8* со звёздочкой

Настройте автообнаружение и прикрепление к хостам созданного вами ранее шаблона.

#### Требования к результату
- [ ] Прикрепите в файл README.md скриншот правила обнаружения, а также скриншот страницы Discover, где видны оба хоста.*

Создаем action discovery, хосты будут добавлены в группу homework с нашим шаблоном:

![screen](https://github.com/igorsprint-code/hw-03/blob/main/Screenshot_3.jpg)

Указывает диапазон ip-aдресов:

![screen](https://github.com/igorsprint-code/hw-03/blob/main/Screenshot_4.jpg)


Оба хоста обнаружены:

![screen](https://github.com/igorsprint-code/hw-03/blob/main/Screenshot_5.jpg)






 ---



1. Выполнено минимум 4 обязательных задания
2. Прикреплены требуемые скриншоты, код и файлы 
3. Задание оформлено в шаблоне с решением и опубликовано на GitHub
