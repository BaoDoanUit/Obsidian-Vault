@startuml
start 
:Prospect Account;
:Historical Usage Req;
:Historical Usage Resp;
:Load Forecast;
:Account Pricing Run;
:Product Offering;
:Contract and T&Cs;
:Excute & Verify;
if (Customer Enrollment) then (Valid)
   :CES|Blue Enrollment;
   :EDI Enroll Request;
   if (EDI Enroll Response) then (Accept)
   else (Reject)
   :Correct Data Issue;
   endif
else (In valid)
   :Correct Data Issue; 
endif
:Begin Load FLow;
@enduml