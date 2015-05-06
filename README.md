## Hide messages in sc2tv.ru chat

This is a greasemonkey script for Firefox that completely hides 
messages of users with particular roles in the sc2tv.ru chat.

Initially it is used to hide moderator's messages.

Request for modification due to rating wipe on sc2tv.

1. Release 1 (4 mh): introducing new roles.
    1. The script should keep a map of pairs for special users: nickname -> user_role.
    2. So far there can be 3 user roles: a foe, a girl, and a friend.
    3. Foes (ignored users) are either removed altogether or only their nicknames are kept visible. This option is hardcoded as a
     constant.
    4. Girls (only theskymaybe so far) are highlighted by the colour '#FFC0CB' 
    5. Friends are highlighted by a colour combination that is hardcoded (a corresponding style should be set as a constant 
     at the beginning of the script.
    6. The roles are mutually exclusive and have the next priorities: foe > girl > friend. 
    7. Ignoring by the role is removed (probably temporarily).
    8. For the first release the hash is hardcoded. 
  
2. Release 2:  user hash management.
    1. The hash should be serialized and deserialized in JSON format.
    2. It should be stored and restored using GM_setvalue / GM_getvalue.
    3. 