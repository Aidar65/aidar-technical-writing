# Р”РѕРєСѓРјРµРЅС‚РёСЂРѕРІР°РЅРёРµ РјРѕРґСѓР»СЏ Р·Р°С‰РёС‚С‹ РўРџРђ (CODESYS ST)

Р РµР°Р»РёР·Р°С†РёСЏ РїСЂРѕРіСЂР°РјРјРЅРѕР№ Р±Р»РѕРєРёСЂРѕРІРєРё СЌР»РµРєС‚СЂРѕРїСЂРёРІРѕРґР° РїСЂРё РїСЂРµРІС‹С€РµРЅРёРё РєСЂСѓС‚СЏС‰РµРіРѕ РјРѕРјРµРЅС‚Р° РїРѕ Р“РћРЎРў 33260.

```pascal
FUNCTION_BLOCK FB_ValveTorqueProtection
VAR_INPUT
    rCurrentTorque : REAL; // РўРµРєСѓС‰РёР№ РєСЂСѓС‚СЏС‰РёР№ РјРѕРјРµРЅС‚ (РќРј)
    rMaxTorque     : REAL; // РџСЂРµРґРµР»СЊРЅС‹Р№ РґРѕРїСѓСЃРє РїРѕ РўРЈ (РќРј)
    bEmergencyStop : BOOL; // РђРІР°СЂРёР№РЅР°СЏ РєРЅРѕРїРєР°
END_VAR
VAR_OUTPUT
    bTripAlarm     : BOOL; // РЎРёРіРЅР°Р» РѕС‚СЃРµС‡РєРё РїСЂРёРІРѕРґР°
END_VAR

IF (rCurrentTorque >= rMaxTorque) OR bEmergencyStop THEN
    bTripAlarm := TRUE;
ELSE
    bTripAlarm := FALSE;
END_IF;
END_FUNCTION_BLOCK

