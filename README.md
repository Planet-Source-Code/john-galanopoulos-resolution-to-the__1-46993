<div align="center">

## Resolution to the


</div>

### Description

Finally a valid resolution to this strange Oracle error.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[John Galanopoulos](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/john-galanopoulos.md)
**Level**          |Intermediate
**User Rating**    |5.0 (15 globes from 3 users)
**Compatibility**  |VB 5\.0, VB 6\.0, VB Script, ASP \(Active Server Pages\) 
**Category**       |[Debugging and Error Handling](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/debugging-and-error-handling__1-26.md)
**World**          |[Visual Basic](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/visual-basic.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/john-galanopoulos-resolution-to-the__1-46993/archive/master.zip)





### Source Code

<h2 style="COLOR: midnightblue">The "ORA-01843" Error; How-Not-To </h2>
<P> </P>
<P>I have seen many developers (<EM>specifically those who deal with ORACLE
backends</EM>) knocking themselves out (i was one of them) with this strange
error while trying to execute an SQL query with a date field in it. </P>
<P>For some strange reason, Oracle seems to react with your date format
'mm/dd/yyyy' (or 'dd/mm/yyyy') <br>and raises this error.</P>
<P>The first thing i did, was to check whether the registry value
HKEY_LOCAL_MACHINE\Software\ORACLE\nls_date_format  was of the format
"dd/mm/yyyy".</P>
<P> And it was!! After i tried many things, i returned to that key and i
changed the format. Still nothing. This key seems to have no effect to the way
ORACLE databases handle date values.</P>
<P>I went back to my source and after the line where my connection to the
ORACLE database was initialized, i wrote :</P>
<P style="COLOR: mediumblue">strSQL  = "ALTER SESSION SET NLS_DATE_FORMAT =
'DD/MM/YYYY'"</P>
<P>{The following line applies to Oracle Objects for OLE ( aka OO4O). If
you use ADO, RDO, DAO, ODBC API etc etc write it in it's relative format}.</P>
<P style="COLOR: mediumblue"> myOraDB.ExecuteSQL (strSQL)</P>
<P>
 Guess what ppl. It worked!</P>
<P>All my Insert/Update/Delete SQL statements that included a date value where
properly inserted into the Oracle database table. No errors so no problems :-)</P>
<br> More oracle tips at http://aboutoracle.blogspot.com<br>

