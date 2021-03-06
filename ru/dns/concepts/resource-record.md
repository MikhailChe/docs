# Ресурсные записи

Ресурсная запись — это главная единица информации в DNS. С помощью ресурсных записей вы определяете, куда направить запросы, поступающие на определенные доменные имена. У ресурсных записей есть следующие параметры:

* Доменное имя.
* Тип записи.
* Время жизни записи (TTL, Time to live) в секундах до актуализации информации о значении записи.
* Значение записи.  

{{ dns-name }} оперирует наборами записей. Набор может содержать одну запись или объединять ресурсные записи с одинаковым именем и типом, но с разными значениями.

Пример набора записей:

Имя | Тип | TTL | Значение
----- | ----- | ----- | -----
example.com | A | 600 | 10.0.0.1
example.com | A | 600 | 10.0.0.2
example.com | A | 600 | 10.0.0.3

Наборы записей можно изменять, добавляя или удаляя записи.

## Типы ресурсных записей {#rr-types}

{{ dns-name }} поддерживает следующие типы ресурсных записей:

### A {#a}

`A` — сопоставление доменного имени и IPv4-адреса. Например, запрос A-записи `www.example.com` должен вернуть IPv4-адрес вида `xxx.xxx.xxx.xxx`.

Имя | Тип | TTL | Значение
----- | ----- | ----- | -----
example.com. | A | 600 | 10.0.0.100

### MX {#mx}

`MX` — имя сервера, обрабатывающего электронную почту, например `mail.example.com`. MX-записи позволяют задать приоритет серверов для обработки электронной почты. MX-запись должна указывать на A- или AAAA-запись. 
  
Имя | Тип | TTL | Значение
----- | ----- | ----- | -----
example.com. | MX | 600 | 10 mail1.example.com.
example.com. | MX | 600 | 50 mail2.example.com.

### CNAME {#cname}

`CNAME` — псевдоним для FQDN. С помощью CNAME можно обращаться к разным службам, работающим на одном IP-адресе. Например, CNAME-записи `first.example.com` и `second.example.com` могут указывать на одну A-запись `example.com`. 

Имя | Тип | TTL | Значение
----- | ----- | ----- | -----
first.example.com. | CNAME | 600 | example.com
second.example.com. | CNAME | 600 | example.com
example.com. | A | 600 | 10.0.0.100

### SRV {#srv}

`SRV` — запись, указывающая имя хоста и порт сервера, на которых работает определенная служба. SRV-запись должна указывать на A- или AAAA-запись. При создании записи указываются приоритет и вес сервера при распределении запросов — так можно распределять нагрузку не только между группами серверов, но и внутри групп из нескольких серверов. Клиент обращается к серверу с наименьшим числом приоритета и если приоритеты одинаковые у нескольких серверов, распределяет запросы согласно весам.
  
Имя | Тип | TTL | Значение
----- | ----- | ----- | -----
_sip._tcp.example.com. | SRV | 600 | 10 70 8080 farm1.example.com.
_sip._tcp.example.com. | SRV | 600 | 10 20 8080 farm2.example.com.
_sip._tcp.example.com. | SRV | 600 | 10 10 8080 farm3.example.com.
_sip._tcp.example.com. | SRV | 600 | 20 0 8080 farm4.example.com.

### AAAA {#aaaa}

`AAAA` — сопоставление доменного имени и IPv6-адреса. Работает аналогично A-записям.

### PTR {#ptr}

`PTR` — сопоставление IP-адреса и доменного имени. Автоматическое создание PTR-записей доступно только во внутренних зонах.

### TXT {#txt}

`TXT` — произвольная запись.

### SOA {#soa}

`SOA` — запись, содержащая базовую информацию о зоне. Создается автоматически.

### NS {#ns}

`NS` — запись, содержащая адреса серверов имен. Адреса серверов по умолчанию можно указать у вашего регистратора, чтобы делегировать домен. NS-записи используются для делегирования доменов на другой авторитетный сервер.