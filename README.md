le_rsyslog
==========
le_rsyslog is a Python tool which quickly allows you to configure your Rsyslog without needing to edit any configuration files

Logentries lersyslog version 1.0.9
Usage: lersyslog COMMAND [ARGS]

```python
Where command is one of:
    register                           Register this host
    follow {file1, file2, ... ,fileN}  Follow given files
    import                             Import a JSON file to use to configure Rsyslog
    help                               Show this message and exit

Where parameters are:
    --version          Show version number
    --host-key=        Set host key and exit
    --account-key=     Set account key and exit
    --use-ca-provided  Use internal bundled certificate
    --force            Force given operation
    --debug            Switch on debug messages
```
Register le_rsyslog
---
To use le_rsyslog you will be first required to registered it. This can be done by running the command below and following the instructions. Note you will need a [Logentries Account](https://logentries.com/quick-start/) to register.

```
sudo python lersyslog register
```

You can automate this step by providing your [Account Key](https://logentries.com/doc/accountkey/) as a parameter instead.

```
sudo python lersyslog register --account-key=MY_ACCOUNT_KEY
```
Once run this will automatically create a new Host inside of your Logentries Account. If you wish to use an existing Host then you can specify a Host Key by usering the ```host-key=``` parameter while registering.


Following a file
---
After registering the application you can follow a file by running the following command.

```
sudo python lersyslog follow myfile
```
Where myfile is some logical file in your File System. le_rsyslog will then automatically create a [Token TCP](https://logentries.com/doc/input-token/) log in your Logentries Account which will be used to send the log data from your followed file to.


Importing a JSON Configuration file
---
le_rsyslog has the ability to import a json configuration file which allows the it to configure Rsyslog to follow certain log files and send to a particular token. This system is useful for elastic enviroments where you want a single configuration file to be across all servers when they are brought up.

The JSON configuration file requires the following format to be present

```json
{
    "logs": [
        {
            "path": "/home/stephen/log1.log",
            "name": "test.log",
            "token": "LOG_TOKEN_ONE"
        },
        {
            "path": "/home/stephen/log2.log",
            "name": "test.log",
            "token": "LOG_TOKEN_TWO"
        }
    ]
}
```

Where LOG_TOKEN_ONE and LOG_TOKEN_TWO are [Log Tokens](https://logentries.com/doc/input-token/) that were created in Logentries.

Using this configuration file your Rsyslog will be configured to follow each file and use the associated Token when sending to Logentries.
