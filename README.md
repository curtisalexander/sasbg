# sasbg
Run a SAS program in the background, optionally redirecting the SAS log

## Features
* Run a SAS program using `nohup`
* Redirect stdout and stderr to `/dev/null`
* Optionally redirect the log
* Optionally redirect the log, appending the execution datetime to the log filename
* If neither log option `--log` nor `--logdt` is used then redirect the log to the same directory as the SAS program (rather than to the directory from which the script was called)
* If either log option `--logdt` or `--dt` is used then append the execution datetime to the log filename to enable repeated running of a SAS program without overwriting the log
* Throws an error if the user attempts to write out a log with `*.sas` extension as this could potentially overwrite the executing SAS program

## Usage
```
sasbg [option...] [SAS program]

    -h, --help          display help
    -l, --log <file>    redirect log
    --logdt <file>      redirect log, appending datetime to log filename
    --dt                append datetime to log filename, writing log to
                          same directory as SAS program
```

## Examples
```
sasbg --log '/dir/to/log/myprogram.log' myprogram.sas     # write log to specific directory
sasbg --logdt '/dir/to/log/myprogram.log' myprogram.sas   # write log with datetime appended to
                                                          #   log filename to specific directory
sasbg myprogram.sas           # write log to same directory as SAS program
sasbg --dt myprogram.sas      # write log with datetime appended to log filename
                              #   to same directory as SAS program
```

## Requirements
* Assumes the `sas` executable is within the user's `$PATH`
* Requires the command `readlink`
