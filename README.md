# access-system-database-files

### Useful input syntax:
- validend and validstart timestamp: 'yyyy-mm-ddThh:mm:ssZ'

# UserData
- First_Name varchar(20)
- Last_Name varchar(20)
- Email_Address varchar(40)
- Card_Id char(4)
- Card_Pin char(4)
- Valid_Start timestamp
- Valid_End timestamp
## Functions:
### AddUser()
Syntax: 
select * from adduser('CardId','CardPin','Email','Firstname','Lastname','Validend','Validstart');
Side effect: Adds user to Userdata table
returns true if added
returns false if table not found
### UpdateUser()
Syntax: select * from updateuser('CardId','CardPin','Email','Firstname','Lastname','PreviousCardId','Validend','Validstart');
Side effects: Updates existing user in Userdata table
returns true if user updated
returns false if user not found
### GetUserBase()
Syntax: GetUserBase: select * from GetUserbase();
Side effects: none
returns UserData table
### GetUser()
Syntax: GetUser: select * from GetUser('CardId_');
Side effects: none
returns Userdata table where CardId_ = Card_id
### PeekUser()
Syntax: select * from peekuser('CardId_');
Side effects: none
returns true if user with CardId_ found
returns false if user with CardId_ not found
### RemoveUser()
Syntax: select * from RemoveUser('CardId_')
Side effect: Removes user from UserData table with condition CardId_ = Card_Id
returns true if user found and removed
returns false if user not found
### ValidateUser()
Syntax: select * from ValidateUser('CardId_','CardPin_')
Side effect: none
returns true if CardId_ and CardPin is found in same row in UserData
returns false if not found

# AccessLog
- Card_Id char(4)
- Approved_Entry bool
- Time_Of_Entry timestamp
- Door_Number varchar(4)

## Functions:

### Log()
Syntax: select * from Log('CardId_','ApprovedEntry_', 'TimeOfEntry_', 'DoorNumber_')
Side effect: Adds new accesslog data to AccessLog table
returns true if added
returns false if table not found
### DoorReport()
Syntax: select * from DoorReport('doorNumber_','startDate_','endDate_')
returns table from AccessData where doorNumber_ = door_number and Between startDate_ and endDate_
### Report()
Syntax: select * from DoorReport('doorNumber_','startDate_','endDate_')
returns table from AccessData where Between startDate_ and endDate_
### SuspiciousUsers()
Syntax: select * from DoorReport()
returns table with users who has approved_entry = false >= 10
# AlarmLog
- Time_Of_Alarm timestamp
- Door_Number varchar(4)
- Alarm_Type varchar(7)










