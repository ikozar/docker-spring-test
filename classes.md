@startuml

!theme plain
top to bottom direction
skinparam linetype ortho

class DEVICES {
   REX_CONNECTED_CODE: character varying(255)
   BATTERY: integer
   CODE: character varying(6)
   DEVICE_TYPE: character varying(255)
   IS_ACTIVE: boolean
   NAME: character varying(255)
   SIGNAL_LEVEL: integer
   DEVICESIA_UID: uuid
   ROOM_UID: uuid
   UID: uuid
}
class DEVICES_DATA {
   PARAM1: character varying(255)
   PARAM10: character varying(255)
   PARAM2: character varying(255)
   PARAM3: character varying(255)
   PARAM4: character varying(255)
   PARAM5: character varying(255)
   PARAM6: character varying(255)
   PARAM7: character varying(255)
   PARAM8: character varying(255)
   PARAM9: character varying(255)
   UID: uuid
}
class DEVICES_INNER_DEVICES {
   PROTECTOR_UID: uuid
   INNER_DEVICES_UID: uuid
}
class DEVICES_SETTINGS {
   BOOL_SETT1: boolean
   BOOL_SETT10: boolean
   BOOL_SETT2: boolean
   BOOL_SETT3: boolean
   BOOL_SETT4: boolean
   BOOL_SETT5: boolean
   BOOL_SETT6: boolean
   BOOL_SETT7: boolean
   BOOL_SETT8: boolean
   BOOL_SETT9: boolean
   INT_SETT1: integer
   INT_SETT2: integer
   INT_SETT3: integer
   INT_SETT4: integer
   INT_SETT5: integer
   STR_SETT1: character varying(255)
   STR_SETT2: character varying(255)
   STR_SETT3: character varying(255)
   STR_SETT4: character varying(255)
   STR_SETT5: character varying(255)
   UID: uuid
}
class DEVICES_SIA {
   ID: bigint
   MULTI_UID: uuid
   NAME: character varying(255)
   NORM: integer
   ROLE: integer
   TYPE: integer
   UID: uuid
}
class HUBS {
   IP4ADDRESS: character varying(255)
   ALERT: boolean
   SECURITY: boolean
   NAME: character varying(255)
   OWNER_UID: uuid
   UID: uuid
}
class HUBS_USERS {
   HUBS_UID: uuid
   USERS_UID: uuid
}
class NOTIFICATIONS {
   CONTENT: character varying(255)
   CREATED: timestamp
   HUB_UID: uuid
   IS_READ: boolean
   IS_SENT: boolean
   TG_SENT: boolean
   TITLE: character varying(255)
   TYPE: character varying(255)
   USER_UID: uuid
   DEVICE_UID: uuid
   ID: bigint
}
class ROOMS {
   NAME: character varying(255)
   HUB_UID: uuid
   UID: uuid
}
class ROOMS_DEVICES {
   ROOMS_UID: uuid
   DEVICES_UID: uuid
}
class SCRIPTS {
   ICON_ID: integer
   IS_ACTIVE: boolean
   IS_PINNED: boolean
   NAME: character varying(255)
   HUB_UID: uuid
   UID: uuid
}
class SCRIPTS_DEVICES {
   SCRIPTS_UID: uuid
   DEVICES_UID: uuid
}
class SCRIPTS_ROOMS {
   SCRIPTS_UID: uuid
   ROOMS_UID: uuid
}
class USERS {
   EMAIL: character varying(255)
   FIRST_NAME: character varying(255)
   LAST_HUB_UID: uuid
   LOGIN: character varying(255)
   PASSWORD: character varying(255)
   ROLE: smallint
   SECOND_NAME: character varying(255)
   SEND_ME_EMAIL_NOTIFICATION: boolean
   TG_CHAT_ID: bigint
   UID: uuid
}

DEVICES                -[#595959,plain]-^  DEVICES_SIA           : "DEVICESIA_UID:UID"
DEVICES                -[#595959,plain]-^  ROOMS                 : "ROOM_UID:UID"
DEVICES_INNER_DEVICES  -[#595959,plain]-^  DEVICES               : "INNER_DEVICES_UID:UID"
DEVICES_INNER_DEVICES  -[#595959,plain]-^  DEVICES               : "PROTECTOR_UID:UID"
HUBS                   -[#595959,plain]-^  USERS                 : "OWNER_UID:UID"
HUBS_USERS             -[#595959,plain]-^  HUBS                  : "HUBS_UID:UID"
HUBS_USERS             -[#595959,plain]-^  USERS                 : "USERS_UID:UID"
NOTIFICATIONS          -[#595959,plain]-^  DEVICES               : "DEVICE_UID:UID"
ROOMS                  -[#595959,plain]-^  HUBS                  : "HUB_UID:UID"
ROOMS_DEVICES          -[#595959,plain]-^  DEVICES               : "DEVICES_UID:UID"
ROOMS_DEVICES          -[#595959,plain]-^  ROOMS                 : "ROOMS_UID:UID"
SCRIPTS                -[#595959,plain]-^  HUBS                  : "HUB_UID:UID"
SCRIPTS_DEVICES        -[#595959,plain]-^  DEVICES               : "DEVICES_UID:UID"
SCRIPTS_DEVICES        -[#595959,plain]-^  SCRIPTS               : "SCRIPTS_UID:UID"
SCRIPTS_ROOMS          -[#595959,plain]-^  ROOMS                 : "ROOMS_UID:UID"
SCRIPTS_ROOMS          -[#595959,plain]-^  SCRIPTS               : "SCRIPTS_UID:UID"
@enduml
