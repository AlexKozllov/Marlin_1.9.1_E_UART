# Marlin_1.9.1_E_UART

# Настроена переходная характеристика переключения режимов spreadCycle & stealthchop

# Решена проблема инициализации драйверов подключенных по UART связаная с задежкой подачи 24В на плату драйвера

в файле Marlin_main.ccp в на встроках с 15250-15253 добавленна задержка инициализации softwear serial UART (добавлена строка [code]safe_delay(2000);[/code])
Было:
[code]
#if HAS_DRIVER(TMC2208)
tmc2208_serial_begin();
#endif
[/code]

Стало:
[code]
#if HAS_DRIVER(TMC2208)
safe_delay(2000);
tmc2208_serial_begin();
#endif
[/code]

# Функция постройки карты стола временно отключена, но в качестве Z_endstop_min используется индуктивный датчик
