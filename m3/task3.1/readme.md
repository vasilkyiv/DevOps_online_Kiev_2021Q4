
[DevOps_online_Kiev_2021Q4 (MY GITHUB URL REPO)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4.git)
=======================================

[MODULE 03 NETWORKING](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m3) 
===========================================================================
> # [TASK_3.1 Створення мереж Home Office, Enterprise, Data Center.](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m3)


> 1. Створити мережі, як показано на рис. 1. Рекомендовані моделі комутаторів Catalyst 2960, безпровідний маршрутизатор – WRT300N. В мережі Data Center підключити сервери до портів відповідно рис. 1

[![*Report in screenshots*](shreenshot/1.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m3/task3.1)

> 2. В мережі Enterprise призначити статичні адреси, сформовані за таким правилом: Адреса мережі 10.Y.D.0/24, де Y – дві останні цифри з вашого року народження, D – дата народження. Хостова частина адреси Client 1 – 10, Client 2 – 20, DHCP Server – 100. Наприклад, якщо ви народились 25-го квітня 1999 р., то адреса мережі буде 10.99.25.0/24, а адреса Client 1- 10.99.25.10/24

> 3. Перевірити зв'язок за допомогою команди ping

- ###   DHCP SERVER - 10.83.10.100/24
- ###   CLIENT 1    - 10.83.10.10/24
- ###   CLIENT 2    - 10.83.10.20/24

[![*Report in screenshots*](shreenshot/2.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m3/task3.1)

> 4. В мережі Data Center призначити статичні адреси, сформовані за таким правилом: M.D.Y.0/24, де М – номер місяця народження, D і Y аналогічно попередньому. Хостова частина Web Server 1 – 50, Web Server 2 – 100, DNS Server – 150. Таким чином адреса DNS Server буде 4.25.99.150

> 5. Перевірити зв'язок за допомогою команди ping

- ###   WEB SERVER 1 - 3.10.83.50/24
- ###   WEB SERVER 2 - 3.10.83.100/24
- ###   DNS - 3.10.83.150/24

[![*Report in screenshots*](shreenshot/3.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m3/task3.1)

> 6. На комп’ютері Client 3 замінити мережевий адаптер Ethernet на адаптер Wi-Fi – модуль PT-HOST-NM-1W, як показано на рис. 2. Результатом успішної заміни є поява бездротового зв’язку, як показано на рис. 1

> 7. Призначити Сlient3 статичну адресу 192.168.0.(D+10). Для нашого прикладу це буде 192.168.0.35.

###   CLiENT 3 - 192.168.0.20/24

[![*Report in screenshots*](shreenshot/4.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m3/task3.1)


###  Додаткове завдання: Дослідження структури пакету за допомогою аналізатора пакетів Wireshark.

> 1. Інсталювати і запустити програму Wireshark.

> 2. Вибрати інтерфейс для захоплення трафіку (меню Capture/nterface)та активізувати режим захоплення.

> 3. Скопіювати через мережу файл розміром кілька десятків Мбайт.

> 4. Завершити захоплення трафіку та перейти до режиму аналізу.

> 5. Знайти в захопленому потоці TCP –сегмент. Зробити його screenshot.

> 6. В даному сегменті знайти заголовки канального, мережевого і транспортного рівнів. Виділити їх на screenshot.

> 7. В кожному із цих заголовків знайти відповідно МАС-адреси відправника та отримувача, ІР-адреси відправника і отримувача та номери портів відправника і отримувача.

[![*Report in screenshots*](shreenshot/5.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m3/task3.1)

************************
[MODULE 03 NEITORKING](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m3) 
================
> # [Task 3.2  З’єднання окремих мереж за допомогою мережі Internet та налаштування VLAN](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m3)


> 1. З’єднати створені у попередньому Taskу мережі між собою, як показано на рис. 1. Для побудови мережі Internet використати маршрутизатори PT-Empty, попередньо вставивши в них 5 модулів 1CGE, як показано на рис. 2. Switch мережі Enterprise підключити до інтерфейсу GigabitEthernet0/0 (GE0/0) Router ISP1, Switch мережі Data Center підключити до інтерфейсу GigabitEthernet0/0 (GE0/0) Router ISP3, WAN порт Home Router мережі Home Office підключити до інтерфейсу GigabitEthernet0/0 (GE0/0), як показано на рис.1. Маршрутизатори з’єднати між собою через інтерфейси, як показано на рис. 1.

[![*Report in screenshots*](shreenshot/1.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m3/task3.1)

> 2. Для реалізації мережі Internet використати мережу з адресою (D+10).M.Y.0/24, поділивши її на підмережі з префіксом /26.

> ### All 4 of the Possible /26 Networks for 20.3.83.0/24 (20.3.83.*/26)
*******************
> FIRST SUBNET
- Network Address 20.3.83.0 
- Usable Host Range 20.3.83.1 - 20.3.83.62    	255.255.255.192
- Broadcast Address: 20.3.83.63
*************************
> SECOND SUBNET
- Network Address 20.3.83.64 
- Usable Host Range 20.3.83.65 - 20.3.83.126      255.255.255.192
- Broadcast Address: 20.3.83.127
**********************
> THIRD SUBNET
- Network Address 20.3.83.128
- Usable Host Range 20.3.83.129 - 20.3.83.190      255.255.255.192
- Broadcast Address: 20.3.83.191
***********************
> FOURTH SUBNET
- Network Address 20.3.83.192 
- Usable Host Range 20.3.83.193 - 20.3.83.254      255.255.255.192
- Broadcast Address: 20.3.83.255
**********************

> 3. Призначити ІР-адреси інтерфейсам маршрутизаторів за такими правилами: Router ISP1 GE0/0 - 10.Y.D.1/24, Router ISP3 GE0/0 - M.D.Y.1/24. Адреси для решти інтерфейсів маршрутизаторів призначити відповідно до поділу адреси (D+10).M.Y.0/24 на підмережі. Приклад призначення IP адреси інтерфейсу маршрутизатора ISP1 GE0/0 показано на рис. 3. Увага – обов’язково слід увімкнути інтерфейс поставивши позначку в полі «On»
*******************
- ### ROUTER ISP1 GE0/0 - 10.83.10.1/24

- ### ROUTER ISP3 GE0/0 - 3.10.83.1/24
***********************
> ### from ROUTER ISP2 GE0/0 to  HOME ROUTER  
> FIRST SUBNET
- Network Address 20.3.83.0 
- Usable Host Range 20.3.83.1 - 20.3.83.62 	255.255.255.192
- Broadcast Address: 20.3.83.63

- ### ROUTER ISP2 GE0/0 - 20.3.83.1 	255.255.255.192
- ### HOME ROUTER FE0/0 - 20.3.83.2     255.255.255.192
**************************
>  ### from ROUTER ISP2 GE0/1 to  ISP1 GE0/1  
> SECOND SUBNET
- Network Address 20.3.83.64 
- Usable Host Range 20.3.83.65 - 20.3.83.126   255.255.255.192
- Broadcast Address: 20.3.83.127

- ### ROUTER ISP2 GE0/1 - 20.3.83.65 	255.255.255.192
- ### ROUTER ISP1 GE0/1 - 20.3.83.66     255.255.255.192
**************************
> ### from ROUTER ISP1 GE0/2 to  ISP3 GE0/2 
> THIRD SUBNET
- Network Address 20.3.83.128
- Usable Host Range 20.3.83.129 - 20.3.83.190      255.255.255.192
- Broadcast Address: 20.3.83.191 

- ### ROUTER ISP1 GE0/2 20.3.83.129   255.255.255.192
- ### ROUTER ISP3 GE0/2 20.3.83.130   255.255.255.192
***********************
> ### from ROUTER ISP3 GE0/3 to  ISP2 GE0/3 
> FOURTH SUBNET
- Network Address 20.3.83.192 
- Usable Host Range 20.3.83.193 - 20.3.83.254      255.255.255.192
- Broadcast Address: 20.3.83.255

- ### ROUTER ISP3 GE0/2 20.3.83.193   255.255.255.192
- ### ROUTER ISP2 GE0/2 20.3.83.194   255.255.255.192

> 4. На комп’ютерах вказати адреси відповідні адреси шлюзів (Default Gateway) 
> 5. Перевірити зв'язок комп’ютерів з власними шлюзами за допомогою команди ping

[![*Report in screenshots*](shreenshot/6.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m3/task3.1)

# Налаштування VLAN в Data Center

> 6. Перевірити зв’язок між серверами за допомогою команди ping та маршрут проходження пакета за допомогою tracert

> 7. Змінити маску підмережі на серверах на 255.255.255.192

> 8. Повторити пункт 6 та зафіксувати і пояснити зміни 

>9. Змінити приналежність портів Switch Data Center VLAN таким чином: FE0/2 – VLAN2, FE0/3 – VLAN3, FE0/4 – VLAN4. Для цього на Switch Data Center створити відповідні додаткові VLAN, як показано на рис.4, та увести відповідні порти до відповідних VLAN, як показано на рис. 5.

[![*Report in screenshots*](shreenshot/7.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m3/task3.1)

> 10. Повторити пункт 6 та зафіксувати і пояснити зміни

> 11. Для тих, хто буде робити додаткове завдання, перейти до пункту 12, в іншому випадку необхідно повернути порти FE0/2, FE0/3, та FE0/4 до VLAN1. Також бажано відновити маску підмережі на серверах до 255.255.255.0
**************************
## Налаштування маршрутизації між VLAN (додаткове завдання) 

> 12. Для налаштування маршрутизації між VLAN необхідно перевести порт FE0/1 Data Center switch в режим trunk, як показано на рис.6

[![*Report in screenshots*](shreenshot/8.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m3/task3.1)

> 13. Увага! Наступні налаштування необхідно виконувати на маршрутизаторі Router ISP3 в режимі CLI. Перш ніж виконувати наступні кроки необхідно видалити на інтерфейсі Router ISP3 GE0/0 IP-адресу, як показано на рис. 7.

[![*Report in screenshots*](shreenshot/9.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m3/task3.1)

> 14. Перейти в режим CLI на маршрутизаторі, створити три subinterface і налаштувати їх, як показано нижче. В ІР-адресах замість перших трьох одиниць поставити M.D.Y

[![*Report in screenshots*](shreenshot/10.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m3/task3.1)

> 15. На Web Server1, Web Server2 та DNS Server вказати шлюзами адреси M.D.Y.1, M.D.Y.65 та M.D.Y.129 відповідно 

> 16. Перевірити працездатність за допомогою команди ping з одного сервера на інший.

[![*Report in screenshots*](shreenshot/11.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m3/task3.1)

************************
[MODULE 03 NETWORKING](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m3) 
================
> # [Task 3.3  Налаштування маршрутизації](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m3)

Нехай в результаті поділу магістральної мережі (Рис.1) на підмережі були призначені адреси інтерфейсам маршрутизаторів, як показано в таблиці 1.
****************************************************************
| Router | Interface | Network IP-address  | Host IP-address    |
|:-------|:---------:| -------------------:|-------------------:|
| ISP1   | GE0/0     |***10.83.10.0/24***  |***10.83.10.1/24*** |
|        | GE1/0     |***20.3.83.64/26***  |***20.3.83.66/26*** |
|        | GE2/0     |***20.3.83.128/26*** |***20.3.83.129/26***|
| ISP2   | GE0/0     |***20.3.83.0/26***   |***20.3.83.1/26***  |
|        | GE1/0     |***20.3.83.64/26***  |***20.3.83.65/26*** |
|        | GE3/0     |***20.3.83.192/26*** |***20.3.83.194/26***|
| ISP3   | GE0/0.2   |***3.10.83.0/26***   |***3.10.83.1/26***  |
|        | GE0/0.3   |***3.10.83.64/26***  |***3.10.83.65/26*** |
|        | GE0/0.4   |***3.10.83.128/26*** |***3.10.83.129/26***|
|        | GE2/0     |***20.3.83.128/26*** |***20.3.83.130/26***|
|        | GE3/0     |***20.3.83.192/26*** |***20.3.83.193/26***|
| HOME   | INTERNET  |***20.3.83.0/26***   |***20.3.83.2/26***  | 
*****************************************************************

1. Налаштувати таблиці маршрутизації на маршрутизаторах ISP1, ISP2 та ISP3. В таблиці маршрутизації слід вносити тільки віддалені мережі. Наприклад, на Router ISP2 необхідно вказати маршрути тільки до мереж 10.99.25.0/ та 4.25.99.0/24. Мережу 192.168.0.0 в таблиці маршрутизаторів ISP1, ISP2 та ISP3 заносити нетреба, оскільки вона знаходиться під NAT. Приклад налаштування маршрутизації на Router ISP2 наведено на рис. 2.

2. Налаштувати маршрутизацію на бездротовому маршрутизаторі Home Router, для чого додати Default маршрут на Router ISP2, як показано на рис. 3

[![*Report in screenshots*](shreenshot/12.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m3/task3.1)

[![*Report in screenshots*](shreenshot/13.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m3/task3.1)

[![*Report in screenshots*](shreenshot/14.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m3/task3.1)

> 3. Перевірити працездатність мережі за допомогою команди ping та tracert. Остання команда дозволить проконтролювати маршрут пакету. На рис.4 наведено результати tracert з Client 1 на Web Server 2.

[![*Report in screenshots*](shreenshot/15.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m3/task3.1)

> 4. З таблиць маршрутизації маршрутизаторів ISP1, ISP2 та ISP3 видалити статичні записи.

> 5. На маршрутизаторах ISP1, ISP2 та ISP3 налаштувати протокол RIP, для чого вказати перелік безпосередньо приєднаних мереж у класовому форматі, як показано на рис.5 для ISP1.

[![*Report in screenshots*](shreenshot/16.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m3/task3.1)

[![*Report in screenshots*](shreenshot/17.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m3/task3.1)

[![*Report in screenshots*](shreenshot/18.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m3/task3.1)

************************
[MODULE 03 NETWORKING](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m3) 
================
> # [Task 3.4  Налаштування DHCP, DNS, NAT](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m3)

> 1. Налаштувати DHCP Server в Enterprise мережі (рис.1). Для цього увійти в налаштування DHCP Server

> 2. Зробити налаштування DHCP Pool, вказавши початкову адресу 10.Y.D.10 та адресу Default Gateway – адресу інтерфейсу GE0/0 Router ISP1. Зберегти налаштування (кнопка Save) та увімкнути DHCP сервіс (позначка On) на рис.2

[![*Report in screenshots*](shreenshot/19.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m3/task3.1)

> 3. Перевірити працездатність сервісу, поставивши в налаштуваннях Client 1 та Client 2 DHCP, як показано на рис. 3

[![*Report in screenshots*](shreenshot/20.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m3/task3.1)

> 4. Налаштувати DHCP на Home Router та перевірити працездатність на Client 3

[![*Report in screenshots*](shreenshot/21.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m3/task3.1)

[![*Report in screenshots*](shreenshot/22.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m3/task3.1)

5. Для налаштування і перевірки роботи DNS сервісу призначити Web Server1 та Web Server2 доменні імена, наприклад, domain1.com та domain2.com відповідно.


