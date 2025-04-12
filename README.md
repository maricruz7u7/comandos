# comandos
1.--------------
Add-DhcpServerv4Scope -Name "RedInterna" -StartRange 192.168.100.70 -EndRange 192.168.100.100 -SubnetMask 255.255.255.0
2----------------
Set-DhcpServerv4OptionValue -ScopeId 192.168.100.0 -Router 192.168.100.1
3-.--------------------
Set-DhcpServerv4OptionValue -ScopeId 192.168.100.0 -DnsServer 8.8.8.8
4--------------------
Set-DhcpServerv4Scope -ScopeId 192.168.100.0 -State Active
5--------------------
Get-DhcpServerv4Scope
6-------------------
$Antiguo = Get-DhcpServerv4Scope | Where-Object { $_.Name -eq "Antiguo" }
if ($Antiguo) {
    Remove-DhcpServerv4Scope -ScopeId $Antiguo.ScopeId -Force
7--------------------
Get-DhcpServerv4Lease -ScopeId 192.168.100.0
8--------------------
Add-DhcpServerv4Reservation -ScopeId 192.168.100.0 -IPAddress 192.168.100.50 -ClientId "00-11-22-33-44-55" -Description "Reserva Cliente"
9----------------------
Set-DhcpServerv4Scope -ScopeId 192.168.100.0 -State Inactive
10----------------
Export-DhcpServer -Leases -File "C:\Backup\dhcp-export.xml" -Verbose
