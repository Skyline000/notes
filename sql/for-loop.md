# For loop

## MSSQL

```text
DECLARE @_MAX INT
DECLARE @_i INT
DECLARE	@return_value int
 SET @_i = 0
 SET @_MAX = 10 -- 要產生幾筆資料
 WHILE (@_i<@_MAX)
 BEGIN
	--要迴圈的語法
	EXEC @return_value = [dbo].[p_seq_get_nextval2] N'ticket_tran'
	
	--加1
	Set @_i=@_i+1
 END

```





Reference: [https://dotblogs.com.tw/topcat/archive/2010/01/22/13211.aspx](https://dotblogs.com.tw/topcat/archive/2010/01/22/13211.aspx)

