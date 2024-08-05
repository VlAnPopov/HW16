# ДЗ 16 - Сбор и анализ логов

Цель ДЗ - Научится проектировать централизованный сбор логов. Рассмотреть особенности разных платформ для сбора логов.

Задачи:
1. В Vagrant разворачиваем 2 виртуальные машины web и log
2. на web настраиваем nginx
3. на log настраиваем центральный лог сервер на любой системе на выбор
* journald;
* rsyslog;
* elk.
4. настраиваем аудит, следящий за изменением конфигов nginx 
5. Создать третью виртуальную машину, настроить rsyslog на отправку всех логов на центральный сервер логов.

Поставленные задачи решаются с помощью ansible. За-ради разнообразия в использовании ansible настройки nginx и rsyslog на сервере логов забираются в виде готовых конфигов, а на третьей машине - aux - используется специализированная роль robertdebock.rsyslog
