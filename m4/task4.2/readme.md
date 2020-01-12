
In this practical task i've used PS to write data to file, operate with arrays, input and output user data and removed files accepted by some criterias.

File output.
```
Get-Service | Format-table -autosize | out-file K:\Z\ps\export_n.txt -width 1024
```
Array.
```
$a= ,@(1,1,1);
$a+=,@(2,2,2);
$a+=,@(3,3,3);
foreach($i in $a){
    $line = "";
    foreach($j in $i){
        $line += [string]::format("{0}`t", $j);
    }
    $line;
}
Read-Host -Prompt "Press Enter to change a number"
$a[1][1] = 4
foreach($i in $a){
    $line = "";
    foreach($j in $i){
        $line += [string]::format("{0}`t", $j);
    }
    $line;
}
```
![img](https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m4/task4.2/img/replace.png)

User Output

![img](https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m4/task4.2/img/user_out.png)

List of services
```
Get-Service | Sort-Object status | ForEach {
    if ($_.Status -eq "Stopped")
    {
        $color = "red"
    }
    else
    {
        $color = "green"
    }
    Write-Host "$($_.Status) $($_.Name) $($_.DisplayName) " -ForegroundColor $color
}
```
![img](https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m4/task4.2/img/service_rg.png)

HTML Output

![img](https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m4/task4.2/img/process.png)

Even numbers

![img](https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m4/task4.2/img/even.png)

Files create in loop

![img](https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m4/task4.2/img/log.png)

Print count and names

![img](https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m4/task4.2/img/print_names.png)

Count user input

![img](https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m4/task4.2/img/word.png)

Arguments math

![img](https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m4/task4.2/img/math.png)

Compare arguments

![img](https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m4/task4.2/img/arg.png)

Remove files older than 7 days except '.rom' and schedule task.

![img](https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m4/task4.2/img/remove.png)
![img](https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m4/task4.2/img/task.png)