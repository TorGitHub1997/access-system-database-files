# access-system-database-files

### Useful input syntax:
- validEnd_ , validStart_ , startDate_ , endDate_ -> timestamp: 'yyyy-mm-ddThh:mm:ssZ'

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
- Returns true if added
- Returns false if table not found
### UpdateUser()
- Syntax: select * from updateuser('CardId','CardPin','Email','Firstname','Lastname','PreviousCardId','Validend','Validstart');
- Side effects: Updates existing user in Userdata table
- Returns true if user updated
- Returns false if user not found
### GetUserBase()OK
- Syntax: GetUserBase: select * from GetUserbase();
- Side effects: none
- Returns UserData table
- Columns: firstName (varchar), lastName (varchar), card_Id char(4)
### GetUser()OK
- Syntax: GetUser: select * from GetUser('CardId_');
- Side effects: none
- Returns Userdata table where CardId_ = Card_id
- Columns: firstName (varchar), lastName (varchar), emailAddress (varchar), cardId char(4), cardPin (char(4)), validStart (timestamp), validEnd (timestamp)
### PeekUser()
- Syntax: select * from peekuser('CardId_');
- Side effects: none
- Returns bool true if user with CardId_ found
- Returns bool false if user with CardId_ not found
### RemoveUser()
- Syntax: select * from RemoveUser('CardId_')
- Side effect: Removes user from UserData table with condition CardId_ = Card_Id
- Returns bool true if user found and removed
- Returns bool false if user not found
### ValidateUser()
- Syntax: select * from ValidateUser('CardId_','CardPin_')
- Side effect: none
- Returns bool true if CardId_ and CardPin is found in same row in UserData
- Returns bool false if not found

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
- Returns bool true if added
- Returns bool false if table not found
### DoorReport()OK
- Syntax: select * from DoorReport('doorNumber_','startDate_','endDate_')
- Returns table from AccessData where doorNumber_ = door_number and Between startDate_ and endDate_
- Columns: cardId char(4), approvedEntry (char(4)), timeOfEntry (timestamp), doorNumber (varchar(4))
### AccessReport()OK
- Syntax: select * from AccessReport('startDate_','endDate_')
- Side effect: none
- Returns table from AccessData where Between startDate_ and endDate_
- Columns: cardId char(4), approvedEntry (char(4)), timeOfEntry (timestamp), doorNumber (varchar(4))
### SuspiciousUsers()OK
- Syntax: select * from SuspiciousUsers()
- Side effect: none
- Returns table with users who has approved_entry = false >= 10
- Columns: cardId char(4)

# AlarmLog
## Coloums:
- Time_Of_Alarm timestamp
- Door_Number varchar(4)
- Alarm_Type varchar(7)

## Functions:
### AddAlarmLog()
- Syntax: select * from AddAlarmLog('timeOfAlarm_', 'doorNumber_', 'alarmType_)
- Side effect: Adds new Alarm data to AlarmLog table
- Returns true if added
- Returns false if table not found
### AlarmReport()OK
- Syntax: select * from AlarmReport('startDate_','endDate_')
- Side effect: none
- Returns table from AlarmLog where Between startDate_ and endDate_
- Columns: timeOfAlarm timestamp, doorNumber varchar(4), alarmType varchar(7)










