CAS scripts will have native file logging.  Feature available starting in CAS 6.0.1035+  

New log files will be generated in the directory defined within System->File Settings properties.  The filename will use Coordinated Universal Time (UTC) for its date to avoiding conflicts based on region.  Log errors will not prevent scripts from running.

##### System->File Options

![image](https://user-images.githubusercontent.com/5807754/115915373-dc88aa80-a438-11eb-81ba-129eb0b274cd.png)

Option | Description
--|--
Log Directory|Directory storing daily log files.
Log Active|Condition when to write log

Log Active|Description
--|--
None|Disabled
Always|Always write to the temp or user defined directory.
Batch|Only when in batch mode.  Batch mode is true when both File and Script command line parameters are set.
Debug|For deubgging only and should not be used in runtime. Log with debug details for most executed script lines. Debug may write senseitve information to the log file and care should be take to remove these when debugging is complete.

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
SCRIPTRUNTIMEID|GUID|Identifier for script runtime instance 
BATRCHSCRIPT|String|Batch Script Parameter
SCRIPTNAME|String|Current Script
SCRIPTLINE|INT|Current Line
MESSAGE|String|User or Auto-Generated Message

Complex text values are esacped with double-quotes.

#### Example Output

![image](https://user-images.githubusercontent.com/5807754/115920691-2a54e100-a440-11eb-940a-2616174cad73.png)

![image](https://user-images.githubusercontent.com/5807754/116114609-219e1e00-a67f-11eb-9e54-6d5813bc94ea.png)

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

![image](https://user-images.githubusercontent.com/5807754/116114609-219e1e00-a67f-11eb-9e54-6d5813bc94ea.png)
