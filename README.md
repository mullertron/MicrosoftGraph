# MicrosoftGraph

Details from Microsoft
~~~~~
https://docs.microsoft.com/en-us/powershell/module/microsoft.graph.groups/get-mggroup?source=recommendations&view=graph-powershell-1.0
~~~~~

Install Graph 

~~~~~
Install-Module Microsoft.Graph
~~~~~

Check Module is Installed

~~~~~
Get-InstalledModule Microsoft.Graph
~~~~~

Authenticate to Graph

~~~~~
Connect-Graph -Scopes "User.Read","Application.Read.All", "Group.Read.All"
~~~~~

Check Groups

~~~~~
Get-MgGroup
~~~~~


Get Groups and Put them into CSV File

~~~~~
$ojectids = ("6fdedefe-3919-4cdc-bd83-6dda9eb75a59", "ac945a7b-9a7a-4aef-a5ba-4030b52b5e54")
foreach ($objectid in $ojectids)
 {
  $Output = @()
  $ojectids = ("fe537dd2-2111-4d11-bec2-8280edef298f", "fe79b2ed-8c80-41d6-9bb1-cf5f26f9d5e4")
  Get-MgGroup | select Id, DisplayName, Description, GroupTypes, MailEnabled, Mail, AppRoleAssignments, IsAssignableToRole, Owners, MemberOf, Members, SecurityEnabled,
 SecurityIdentifier, OnPremisesSyncEnabled, OnPremisesDomainName | export-csv top1.csv 
 }  
 ~~~~~



~~~~~
$ojectids = ("fe537dd2-2111-4d11-bec2-8280edef298f", "fe79b2ed-8c80-41d6-9bb1-cf5f26f9d5e4")
foreach ($objectid in $ojectids)
{
  $Output = @()

  Get-MgGroup | Format-List Id, DisplayName, Description, GroupTypes, IsAssignableToRole, Owners | Export-Csv output.csv

}  
~~~~~


Find Details of Windows AD groups

~~~~~
https://activedirectorypro.com/find-nested-groups-in-active-directory/#:~:text=%20Find%20Nested%20Groups%20in%20Active%20Directory%20,use%20GUI%20tool%20I%20created%20to...%20More%20
~~~~~

Get Details of Groups from Get-AzureADUserMembership

~~~~~
Connect-AzureAD
$ojectids = get-content "/usr/csuser/clouddrive/users.csv"
foreach ($objectid in $ojectids)

{
  $Output = @()

  Get-AzureADUserMembership -ObjectId $objectid | select @{l='userid';e={$objectid}}, displayname, description  | Export-Csv "/usr/csuser/clouddrive/output.csv" -append

}


$ojectids = ("6fdedefe-3919-4cdc-bd83-6dda9eb75a59", "ac945a7b-9a7a-4aef-a5ba-4030b52b5e54")
foreach ($objectid in $ojectids)

{
  $Output = @()

  Get-AzureADUserMembership -ObjectId $objectid | select @{l='userid';e={$objectid}}, displayname, description  | Export-Csv C:\GPoutput.csv -append

}  
~~~~~


Use Hashtable link

~~~~~

https://devblogs.microsoft.com/scripting/easily-create-a-powershell-hash-table/

~~~~~

Get properties of Get-MgGroup
~~~~~
Get-MgGroup | gm

AcceptedSenders
AdditionalProperties
AllowExternalSenders
AppRoleAssignments
AssignedLabels
AssignedLicenses
AutoSubscribeNewMembers
Calendar
CalendarView
Classification
Conversations
CreatedDateTime
CreatedOnBehalfOf
DeletedDateTime
Description
DisplayName
Drive
Drives
Events
ExpirationDateTime
Extensions
GroupLifecyclePolicies
GroupTypes
HasMembersWithLicenseErrors
HideFromAddressLists
HideFromOutlookClients
Id
IsArchived
IsAssignableToRole
IsSubscribedByMail
LicenseProcessingState
Mail
MailEnabled
MailNickname
MemberOf
Members
MembershipRule
MembershipRuleProcessingState
MembersWithLicenseErrors
Onenote
OnPremisesDomainName
OnPremisesLastSyncDateTime
OnPremisesNetBiosName
OnPremisesProvisioningErrors
OnPremisesSamAccountName
OnPremisesSecurityIdentifier
OnPremisesSyncEnabled
Owners
PermissionGrants
Photo
Photos
Planner
PreferredDataLocation
PreferredLanguage
ProxyAddresses
RejectedSenders
RenewedDateTime
SecurityEnabled
SecurityIdentifier
Settings
Sites
Team
Theme
Threads
TransitiveMemberOf
TransitiveMembers
UnseenCount
Visibility

~~~~~
