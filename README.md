<div align="center">

## Run Program On Startup \(Registry\)


</div>

### Description

Places your program in the Windows Registry so it will run at startup.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[CrAcKeR](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/cracker.md)
**Level**          |Intermediate
**User Rating**    |4.5 (18 globes from 4 users)
**Compatibility**  |Delphi 5, Delphi 4, Pre Delphi 4
**Category**       |[Registry](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/registry__7-36.md)
**World**          |[Delphi](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/delphi.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/cracker-run-program-on-startup-registry__7-144/archive/master.zip)





### Source Code

```
// Place registry in your USES
uses
 Windows, Messages, SysUtils, Classes, Graphics, Controls, Forms, Dialogs, registry, StdCtrls;
// This is the procedure (False means remove, True means create)
procedure RunOnStartup(sProgTitle, sCmdLine: string; bStartup: boolean );
var
 sKey: string;
 reg : TRegIniFile;
begin
 sKey := ''; //sKey := 'Once' if you wish it to only run on the next time you startup.
 if bStartup = false then //If value passed is false, then value deleted from Registry.
 begin
 try
 reg := TRegIniFile.Create( '' );
 reg.RootKey := HKEY_LOCAL_MACHINE;
 reg.DeleteKey(
  'Software\Microsoft'
  + '\Windows\CurrentVersion\Run'
  + sKey + #0,
  sProgTitle);
 reg.Free;
 exit;
 except //Using Try Except so that if value can not be placed in registry, it
 //will not give and error.
 end;
end;
try
 reg := TRegIniFile.Create( '' );
 reg.RootKey := HKEY_LOCAL_MACHINE;
 reg.WriteString(
  'Software\Microsoft'
  + '\Windows\CurrentVersion\Run'
  + sKey + #0,
  sProgTitle,
  sCmdLine );
 reg.Free;
 except
 end;
 end;
```

