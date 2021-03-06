---
external help file: Microsoft.Rtc.Management.Hosted.dll-help.xml
applicable: Skype for Business Online
title: Get-CsStorageServiceConfiguration
schema: 2.0.0
---

# Remove-CsTeamsInteropPolicy

## SYNOPSIS

IMPORTANT: TeamsInteropPolicy has been  replaced by TeamsUpgradePolicy. See description for details. You can also find more guidance here: https://docs.microsoft.com/en-us/MicrosoftTeams/migration-interop-guidance-for-teams-with-skype

This cmdlet previously determined how calls are routed between Skype for Business and Microsoft Teams. It is no longer honored, except if TeamsUpgradePolicy mode=Legacy. However, Legacy mode has been deprecated and customers should update their configurations to use a mode other than Legacy.

## SYNTAX

```
Remove-CsTeamsInteropPolicy [-WhatIf] [-Confirm] [[-Identity] <Object>] [-Tenant <Object>] [-Force] [-AsJob]
```

## DESCRIPTION

IMPORTANT: TeamsInteropPolicy has been replaced by TeamsUpgradePolicy. It is no longer honored by the system, except if TeamsUpgradePolicy has mode=Lgeacy. Legacy mode is being deprecated. Customers that are still using Legacy mode should update their configurations to use a mode other than Legacy. Granting mode=Legacy is now blocked by default, although admins can override this using -Force for the time being. Eventually, the -Force switch will be removed and granting mode=Legacy will not be possible.
 
 
Any customers still using Legacy mode must ensure the following:
 - The global policy must have CallingDefaultClient=ChatDefaultClient, and AllowEndUserClientOverride must be false. If you customized the built-in global policy, undo this by running Remove-CsTeamsInteropPolicy. This will remove the tenant-specific global policy and revert back to the system-wide built-in policy (which cannot be removed). Use the following syntax:
 - `Remove-CsTeamsInteropPolicy -Identity Global`
 - If TeamsInteropPolicy is explicitly assigned to any users, one of these three built-in instances for which CallingDefaultClient = ChatDefaultClient, and for which AllowEndUserClientOverride = false. The other instances are no longer valid configurations, are not supported, and will soon be removed from the system. The valid instances are:
 

**Identity: DisallowOverrideCallingDefaultChatDefault**   
 - AllowEndUserClientOverride: False   
 - CallingDefaultClient: Default   
 - ChatDefaultClient: Default

**Identity: DisallowOverrideCallingSfbChatSfb**   
 - AllowEndUserClientOverride: False   
 - CallingDefaultClient: Sfb   
 - ChatDefaultClient: Sfb

**Identity: DisallowOverrideCallingTeamsChatTeams**   
 - AllowEndUserClientOverride: False   
 - CallingDefaultClient: Teams  
 - ChatDefaultClient: Teams


Use the following cmdlet syntax, where $policy is one of the above values of identity:
`Grant-CsTeamsInteropPolicy -PolicyName $policy -Identity $SipAddress`


For comprehensive documentation on this policy and its settings, see [Migration and interoperability guidance for organizations using Teams together with Skype for Business](https://docs.microsoft.com/en-us/microsoftteams/migration-interop-guidance-for-teams-with-skype).


## EXAMPLES

### -------------------------- Example 1 --------------------------
```
PS C:\> {{ Add example code here }}
```

{{ Add example description here }}

## PARAMETERS

### -Confirm
Prompts you for confirmation before running the cmdlet.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: cf
Applicable: Skype for Business Online 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force
{{Fill Force Description}}

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 
Applicable: Skype for Business Online 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Identity
{{Fill Identity Description}}

```yaml
Type: Object
Parameter Sets: (All)
Aliases: 
Applicable: Skype for Business Online 

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Tenant
{{Fill Tenant Description}}

```yaml
Type: Object
Parameter Sets: (All)
Aliases: 
Applicable: Skype for Business Online 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf
Shows what would happen if the cmdlet runs.
The cmdlet is not run.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: wi
Applicable: Skype for Business Online 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsJob
{{Fill AsJob Description}}

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 
Applicable: Skype for Business Online 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

## INPUTS

### Microsoft.Rtc.Management.Xds.XdsIdentity

## OUTPUTS

### System.Object

## NOTES

This policy has been deprecated. Customters should use TeamsUpgradePolicy to control interop and routing.

## RELATED LINKS

[Migration and interoperability guidance for organizations using Teams together with Skype for Business](https://docs.microsoft.com/en-us/microsoftteams/migration-interop-guidance-for-teams-with-skype)
