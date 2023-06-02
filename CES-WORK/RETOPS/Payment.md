proc get list payment -- blu.usp_payment_select
```sql
-- step 1 
UnAllocatedAmount = UnAllocatedAmount = case when ba.clientIntID = 70 and isnull(p.acntID, 0) > 0 then 0 else  p.PaymentAmt - isnull(a.AllocatedAmount, 0) end

-- step 2
UnAllocatedAmount = p.UnAllocatedAmount - ISNULL(t.TransferAmount, 0),

-- table
blu.tbl_billing_account ba
blu.tbl_payment p
blu.tbl_payment_allocation a
```
![[Payment-1.png]]

proc get list payment -- blu.usp_payment_select
![[Payment-3.png]]
![[Payment-2.png]]