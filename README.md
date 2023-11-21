# access-system-database-files

### Useful input syntax:
- validend and validstart timestamp: 'yyyy-mm-ddThh:mm:ssZ'

# UserData
## Coloums:
- First_Name varchar(20)
- Last_Name varchar(20)
- Email_Address varchar(40)
- Card_Id char(4) (Primary Key)
- Card_Pin char(4)
- Valid_Start timestamp
- Valid_End timestamp
## Functions:
### AddUser()
- Syntax: select * from adduser('CardId','CardPin','Email','Firstname','Lastname','Validend','Validstart');
- Side effect: Adds user to Userdata table
- returns true if added
- returns false if table not found
### UpdateUser()
- Syntax: select * from updateuser('CardId','CardPin','Email','Firstname','Lastname','PreviousCardId','Validend','Validstart');
- Side effects: Updates existing user in Userdata table
- returns true if user updated
- returns false if user not found
### GetUserBase()OK
- Syntax: GetUserBase: select * from GetUserbase();
- Side effects: none
- returns UserData table
- Coloums: firstName (varchar), lastName (varchar), card_Id char(4)
### GetUser()OK
- Syntax: GetUser: select * from GetUser('CardId_');
- Side effects: none
- returns Userdata table where CardId_ = Card_id
-> Coloums: firstName (varchar), lastName (varchar), emailAddress (varchar), cardId char(4), cardPin (char(4)), validStart (timestamp), validEnd (timestamp)
### PeekUser()
- Syntax: select * from peekuser('CardId_');
- Side effects: none
- returns bool true if user with CardId_ found
- returns bool false if user with CardId_ not found
### RemoveUser()
- Syntax: select * from RemoveUser('CardId_')
- Side effect: Removes user from UserData table with condition CardId_ = Card_Id
- returns bool true if user found and removed
- returns bool false if user not found
### ValidateUser()
- Syntax: select * from ValidateUser('CardId_','CardPin_')
- Side effect: none
- returns bool true if CardId_ and CardPin is found in same row in UserData
- returns bool false if not found
  
# AccessLog
## Coloums:
- Card_Id char(4)
- Approved_Entry bool
- Time_Of_Entry timestamp
- Door_Number varchar(4)

## Functions:

### AddAccessLog()
- Syntax: select * from AddAccessLog('CardId_','ApprovedEntry_', 'TimeOfEntry_', 'DoorNumber_')
- Side effect: Adds new accesslog data to AccessLog table
- returns bool true if added
- returns bool false if table not found
### DoorReport()OK
- Syntax: select * from DoorReport('doorNumber_','startDate_','endDate_')
- returns table from AccessData where doorNumber_ = door_number and Between startDate_ and endDate_
-> Coloums: cardId char(4), approvedEntry (char(4)), timeOfEntry (timestamp), doorNumber (varchar(4))
### AccessReport()OK
- Syntax: select * from AccessReport('startDate_','endDate_')
- Side effect: none
- returns table from AccessData where Between startDate_ and endDate_
-> Coloums: cardId char(4), approvedEntry (char(4)), timeOfEntry (timestamp), doorNumber (varchar(4))
### SuspiciousUsers()OK
- Syntax: select * from SuspiciousUsers()
- Side effect: none
- returns table with users who has approved_entry = false >= 10
-> Coloums: cardId char(4)
  
# AlarmLog
## Coloums:
- Time_Of_Alarm timestamp
- Door_Number varchar(4)
- Alarm_Type varchar(7)

## Functions:
### AddAlarmLog()
- Syntax: select * from AddAlarmLog('timeOfAlarm_', 'doorNumber_', 'alarmType_)
- Side effect: Adds new Alarm data to AlarmLog table
- returns true if added
- returns false if table not found
### AlarmReport()OK
- Syntax: select * from AlarmReport('startDate_','endDate_')
- Side effect: none
- returns table from AlarmLog where Between startDate_ and endDate_
-> Coloums: timeOfAlarm timestamp, doorNumber varchar(4), alarmType varchar(7)
  











