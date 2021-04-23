CAS scripts will have native file logging.  Feature available starting in CAS 6.0.1035+  

#### CSV 

CAS will generate a new log files in the directory defined in within System->File Settings properties.  The filename will use the Coordinated Universal Time (UTC) for its date to avoiding conflicts based on region.  Log errors will not prevent script from running.  

##### System->File Options

![image](https://user-images.githubusercontent.com/5807754/115915373-dc88aa80-a438-11eb-81ba-129eb0b274cd.png)

Option | Description
--|--
Log Directory|Directory storing daily log files.
Log Active|Condition when to write log

##### Filename format
cas_script_log_YYYYMMDD.csv

##### Example
![image](https://user-images.githubusercontent.com/5807754/115907462-86af0500-a42e-11eb-871a-d03eb54399d7.png)

#### Format

Column Definition

Name|Type|Format
--|--|--
TIMESTAMP|DateTime|ISO-8601
TYPE|String|INFO, WARN, ERROR and DEBUG
FILE|String|Current File
USER|String|Current User
COMPUTER|String|Computer Name
PROCESSNAME|String|Windows Process Name
PROCESSID|INT|Windows Process ID
BATRCHSCRIPT|String|Batch Script Parameter
SCRIPT|String|Current Script
LINE|INT|Current Line
MESSAGE|String|User or Auto-Generated Message

Complex text values are esacped with double-quotes.

#### Example Output

TIMESTAMP|TYPE|FILE|USER|COMPUTER|PROCESSNAME|PROCESSID|BATCHSCRIPT|SCRIPT|LINE|MESSAGE
--|--|--|--|--|--|--|--|--|--|--
2021-04-23T19:10:59Z,DEBUG,C:\temp\sample1.cas,norbe,DESKTOP-FC6HT0G,dyalog,9068,,Test Log Script,0,Records: 2661
2021-04-23T19:10:59Z,DEBUG,C:\temp\sample1.cas,norbe,DESKTOP-FC6HT0G,dyalog,9068,,Test Log Script,0,Fields: 112
2021-04-23T19:13:51Z,DEBUG,C:\temp\sample1.cas,norbe,DESKTOP-FC6HT0G,dyalog,9068,,Test Log Script,0,Object Type = RecordSet; Records: 2661
2021-04-23T19:13:51Z,DEBUG,C:\temp\sample1.cas,norbe,DESKTOP-FC6HT0G,dyalog,9068,,Test Log Script,0,Object Type = RecordSet; Fields: 112
2021-04-23T19:13:51Z,INFO,C:\temp\sample1.cas,norbe,DESKTOP-FC6HT0G,dyalog,9068,,Test Log Script,2,I'm logging in my script!.
2021-04-23T19:13:53Z,DEBUG,C:\temp\sample1.cas,norbe,DESKTOP-FC6HT0G,dyalog,9068,,Test Log Script,4,
2021-04-23T19:13:53Z,INFO,C:\temp\sample1.cas,norbe,DESKTOP-FC6HT0G,dyalog,9068,,Test Log Subscript,,START
2021-04-23T19:13:53Z,WARN,C:\temp\sample1.cas,norbe,DESKTOP-FC6HT0G,dyalog,9068,,Test Log Subscript,0,Warning test in the subscript.
2021-04-23T19:13:53Z,INFO,C:\temp\sample1.cas,norbe,DESKTOP-FC6HT0G,dyalog,9068,,Test Log Subscript,,SUCCESS
2021-04-23T19:13:53Z,INFO,C:\temp\sample1.cas,norbe,DESKTOP-FC6HT0G,dyalog,9068,,Test Log Script,,SUCCESS

#### How-To

You can write directly to the log using three new scripting methods.

- CasSession.WriteLogInfo
- CasSession.WriteLogError
- CasSession.WriteLogWarn

The methods only need a message(s) to be passed.

#### Example


![image](https://user-images.githubusercontent.com/5807754/115905198-60d43100-a42b-11eb-9bfc-4f6bb8941c8c.png)

##### Script 1 - Test Log Script

```apl
RS ← CasSession.GetCurrentFile''  
  
CasSession.WriteLogInfo 'I''m logging in my script!.'  
  
subScript ← RS.GetItem '\Scripts\Portfolio Summary\Test Log Subscript'  
Shell.ExecuteScript subScript (CharString.New'')
```

##### Script 2 - Test Log Subscript

```apl
CasSession.WriteLogWarn 'Warning test in the subscript.'
```

#### CSV Output

![image](https://user-images.githubusercontent.com/5807754/115905889-63835600-a42c-11eb-8cd2-8e5a92165c3c.png)
