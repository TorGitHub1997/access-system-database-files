# access-system-database-files

How to use the functions

(validend and validstart string: 'yyyy-mm-ddThh:mm:ssZ'
AddUser: select * from adduser('CardId','CardPin','Email','Firstname','Lastname','Validend','Validstart'); 
UpdateUser: select * from updateuser('CardId','CardPin','Email','Firstname','Lastname','PreviousCardId','Validend','Validstart'); 
PeekUser: select * from peekuser('CardId');
RemoveUser: select * from removeuser('CardId');
ValidateUser: select * from validateuser('CardId','CardPin');
GetUserBase: select * from GetUserbase();
GetUser: select * from GetUser('CardId');
