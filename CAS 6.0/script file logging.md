CAS scripts will have two new logging formats; csv and Windows Event Log.

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
