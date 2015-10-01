# sasbg
Run a SAS program in the background, optionally redirecting the SAS log

## Features
* Run a SAS program using `nohup`
* Redirect stdout and stderr to `/dev/null`
* Optionally redirect the log
* Optionally redirect the log, appending the execution datetime to the log filename

## Usage
```
sasbg [option...] [SAS program]

    -h, --help          display help
    -l, --log <file>    redirect log
    --logdt <file>      redirect log, appending datetime to filename
```

## Example
```
$ sasbg --log '/dir/to/log/myprogram.log' myprogram.sas
```

## Requirements
Assumes the `sas` executable is within the user's `$PATH`
