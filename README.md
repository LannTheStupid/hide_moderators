## Hide messages in sc2tv.ru chat

This is a greasemonkey script for Firefox that completely hides 
messages of users with particular roles in the sc2tv.ru chat.

Initially it is used to hide moderator's messages.

Request for modification due to rating wipe on sc2tv.

1. Release 1 (4 mh): introducing new roles.
    1. The script should keep a map of pairs for special users: nickname -> user_role.
    2. So far there can be 3 user roles: a foe, a tyan, and a friend.
    3. Foes (ignored users) are either removed altogether or only their nicknames are kept visible. This option is 
    hardcoded as a constant.
    4. Girls (only theskymaybe so far) are highlighted by the colour '#FFC0CB' 
    5. Friends are highlighted by a colour combination that is hardcoded (a corresponding style should be set 
    as a constant at the beginning of the script.
    6. The roles are mutually exclusive and have the next priorities: foe > tyan > friend. 
    7. Ignoring by the role is removed (probably temporarily).
    8. For the first release the hash is hardcoded. 
  
2. Release 2:  user hash management. (8-12 mh)
    1. The hash should be serialized and deserialized in JSON format.
    2. It should be stored and restored using GM_setvalue / GM_getvalue.
    3. 2 buttons are used to modify the hash:
        1. Ignore/UnIgnore button.
        2. Friend/UnFriend button.
    4. If a user is ignored then his/her ID is inserted into the hash with the "foe" status.
       If a user was a friend or a tyan his/her status changes to "foe".
    5. If a user is befriended then his/her ID is inserted into the hash with the "friend" status.
       If a user already is in the hash (with any status) then nothing happens. 
    6. If a user who was ignored before is unignored his ID is removed from tha hash and he becomes neutral.
    7. If a user who was a friend before is unfriended his ID is removed from the hash and he becomes neutral.
    8. Tyans are changed only by hardcoding.
    9. The button "friend/unfriend" should have the same appearance as "Ignore/UnIgnore" button in the vanilla 
        chat. 
    10.The button "Ignore/UnIgnore" remains the same, but its function changes.
    11.The "ignore" cookie is not used.
    12.The hase is stored after any change.
    
3. Release 3: decoupling dsaving the data and working with the GUI.
    This will be necessary only if users notice a delay after editing friend or foe lists.
    
4. Release 4 (or 3): compressing the hash before storing it.
    This will be necessary only if there are users with really long lists (1024+ symbols in JSON forman).