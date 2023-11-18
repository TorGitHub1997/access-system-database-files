# access-system-database-files
(validend and validstart string: 'yyyy-mm-ddThh:mm:ssZ'
select * from adduser('CardId','CardPin','Email','Firstname','Lastname','Validend','Validstart'); 
select * from updateuser('CardId','CardPin','Email','Firstname','Lastname','PreviousCardId','Validend','Validstart'); 
select * from peekuser('CardId');
select * from removeuser('CardId');
select * from validateuser('CardId','CardPin');
select * from GetUserbase();
select * from GetUser('CardId');
