### Enrollment

```plantuml
EDI -> BLUE


[Enrollment] as E
[Billing_Process] as B

note top of E: Process Enrollment

EDI_Files - E : inbound_process
E ..> HTTP : use

E -> B

database "RETAIL" {
  folder "Information" {
	[tbl_account_info]
  }

  folder "Source" {
	[tbl_enrollment_request]
  }
}

B -> [tbl_account_info]

```


### Billing Process
```plantuml
[Billing] as B
[Invoice] as I
[Statement] as S
[Enrollment] as E

E -> B
B -> S 
S -> I


```


### MPS
```plantuml
start

:Input company and datetime for the last run (DT_Last);
fork 
	:Get records where Created and Modified > DT_Last;
fork again
	:Get records where Created and Modified > DT_Last;
end merge
:Outer Join 2 table above into TableB;


```

```plantuml
top to bottom direction
[HedgeData] as HD
[HedgeDataStage] as HDS
[HedgeDataInterval] as HDI
[HedgeDetailHourly] as HDH
[HedgeStrike] as HS
[HedgeDataIntervalAllocation] as HIA
[HedgeAllocationSchedule] as HAS
[LoadForeCast] as LFC
[LoadForeCastInterval] as LFCI

HDS -> HD
HD -> HDI
HDH -> HDI
HS -> HDI
HDI -> HIA
HAS -> HIA
LFC -> LFCI
```
