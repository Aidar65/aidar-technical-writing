# Документирование модуля защиты ТПА (CODESYS ST)

Реализация программной блокировки электропривода при превышении крутящего момента по ГОСТ 33260.

```pascal
FUNCTION_BLOCK FB_ValveTorqueProtection
VAR_INPUT
    rCurrentTorque : REAL; // Текущий крутящий момент (Нм)
    rMaxTorque     : REAL; // Предельный допуск по ТУ (Нм)
    bEmergencyStop : BOOL; // Аварийная кнопка
END_VAR
VAR_OUTPUT
    bTripAlarm     : BOOL; // Сигнал отсечки привода
END_VAR

IF (rCurrentTorque >= rMaxTorque) OR bEmergencyStop THEN
    bTripAlarm := TRUE;
ELSE
    bTripAlarm := FALSE;
END_IF;
END_FUNCTION_BLOCK
