# Управление приводом ТПА на языке Structured Text (IEC 61131-3)

Программа для ПЛК (CODESYS v3.5) по обработке концевых выключателей и защите двигателя привода от перегрузки по моменту.

---

## 💻 Исходный код блока управления (PLC_PRG)

```iecst
PROGRAM PLC_PRG
VAR
    bLimitSwitchOpen  : BOOL; (* Концевик ОТКРЫТО *)
    bLimitSwitchClose : BOOL; (* Концевик ЗАКРЫТО *)
    rTorqueSensor     : REAL; (* Момент на штоке (Нм) *)
    bMotorEnable      : BOOL; (* Питание пускателя *)
END_VAR

// Защита по крутящему моменту (> 180 Нм — отсечка)
IF rTorqueSensor > 180.0 THEN
    bMotorEnable := FALSE;
END_IF;
