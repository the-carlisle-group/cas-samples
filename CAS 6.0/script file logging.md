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
MESSAGE|String|User Auto-Generated Message
