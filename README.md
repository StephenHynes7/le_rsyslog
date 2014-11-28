le_rsyslog
==========
le_rsyslog is a Python tool which quickly allows you to configure your Rsyslog without needing to edit any configuration files

Logentries lersyslog version 1.0.9
Usage: lersyslog COMMAND [ARGS]

```python
Where command is one of:
    register                           Register this host
    follow {file1, file2, ... ,fileN}  Follow given files
    help                               Show this message and exit

Where parameters are:
    --version          Show version number
    --host-key=        Set host key and exit
    --account-key=     Set account key and exit
    --use-ca-provided  Use internal bundled certificate
    --force            Force given operation
    --debug            Switch on debug messages
