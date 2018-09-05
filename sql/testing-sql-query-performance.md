# Testing SQL query performance



```text
DBCC DROPCLEANBUFFERS
DBCC FREEPROCCACHE 
GO

SELECT * FROM MyTable
```



```text
SET STATISTICS TIME ON
GO

SELECT * FROM MyTable
GO

SET STATISTICS TIME OFF
GO
```



Include Actual Execution Plan \(Ctrl + M\)

Include Client Statistics \(Shift + Alt + S\)

![](../.gitbook/assets/image%20%2820%29.png)

![](../.gitbook/assets/image%20%2829%29.png)

![](../.gitbook/assets/image%20%2863%29.png)



Reference: [https://www.stevefenton.co.uk/2017/04/testing-sql-query-performance/](https://www.stevefenton.co.uk/2017/04/testing-sql-query-performance/)





