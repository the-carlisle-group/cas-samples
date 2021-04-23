CAS scripts will have native file and event logging; CSV and Windows Event Log.

### CSV Format

Column Definition

Name|Type|Format
--|--|--
TIMESTAMP|DateTime|ISO-8601
TYPE|String|INFO,WARN,ERROR
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
2021-04-23T15:11:22Z|INFO|"c:\sample.cas"|"username"|"DESKTOP-FC6HT0G"|"myprocess"|12996||"Portfolio Summary"||"START"
2021-04-23T15:11:23Z|INFO|"c:\sample.cas"|"username"|"DESKTOP-FC6HT0G"|"myprocess"|12996||"Portfolio Summary"|9|"starting wizard"
2021-04-23T15:14:14Z|INFO|"c:\sample.cas"|"username"|"DESKTOP-FC6HT0G"|"myprocess"|12996||"Portfolio Summary"||"SUCCESS"
2021-04-23T15:30:08Z|INFO|"c:\sample.cas"|"username"|"DESKTOP-FC6HT0G"|"myprocess"|12996||"Portfolio Summary"||"START"
2021-04-23T15:30:08Z|INFO|"c:\sample.cas"|"username"|"DESKTOP-FC6HT0G"|"myprocess"|12996||"Portfolio Summary"|9|"starting wizard"
2021-04-23T15:30:18Z|INFO|"c:\sample.cas"|"username"|"DESKTOP-FC6HT0G"|"myprocess"|12996||"Portfolio Summary"||"SUCCESS"
2021-04-23T15:34:43Z|INFO|"c:\sample.cas"|"username"|"DESKTOP-FC6HT0G"|"myprocess"|12996||"Portfolio Summary"||"START"
2021-04-23T15:34:43Z|INFO|"c:\sample.cas"|"username"|"DESKTOP-FC6HT0G"|"myprocess"|12996||"Portfolio Summary"|10|"starting wizard"

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
