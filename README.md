# bugs
1).
https://github.com/MariaDB/server/security/advisories/GHSA-4wgx-ffg9-jrwq
(CVE-2026-107815)

Stack buffer overflow в TYPVAL<double>::SetValue_char(). При чтении значения типа DOUBLE из таблицы TABLE_TYPE='DOS' строка buf[n] = '\0' пишет 0x00 за границы 64-байтного буфера по контролируемому через SQL смещению. Написан рабочий эксплоит (RCE)

2).  https://github.com/ClickHouse/ClickHouse/pull/125661

Для exchange_type = 'headers' каждый ключ из rabbitmq_routing_key_list разбивается по = и безусловно читается matching[1]. Ключ без = (например  'format,logs') приводит к чтению за границами вектора и крашу сервера.

3).
https://github.com/tarantool/tarantool/pull/13394

Для ITER_NP/ITER_PP значение part_count, которое получают из пользовательского IPROTO_KEY, используется для обращения к key_def->parts[part_count - 1] до проверки его размера. Передача массива KEY с количеством элементов больше key_def->part_count приводит к чтению за границами массива и крашу сервера.




